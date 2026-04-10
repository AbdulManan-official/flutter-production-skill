# Performance & Optimization

## Widget Optimization

### const Everything
```dart
// ✅ Good — compile-time constant, never rebuilt
const SizedBox(height: 16)
const Icon(Icons.wifi)
const Text('Connect')

// ❌ Bad — new instance every build
SizedBox(height: 16)
```

### Avoid Rebuilding Parents
```dart
// ❌ Bad — entire list rebuilds when counter changes
class HomeScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Column(children: [
      Text('Count: ${counter.value}'), // causes full rebuild
      ExpensiveListWidget(),
    ]);
  }
}

// ✅ Good — only the Text rebuilds
class HomeScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Column(children: [
      CounterText(),           // isolated rebuild
      const ExpensiveListWidget(), // never rebuilds
    ]);
  }
}

// With GetX: use Obx() at the smallest possible widget level
// With Riverpod: watch providers in leaf widgets, not parents
// With BLoC: use BlocSelector to rebuild only what changed
BlocSelector<CounterBloc, CounterState, int>(
  selector: (state) => state.count,
  builder: (context, count) => Text('Count: $count'),
)
```

---

## Lists & Lazy Loading

### ListView.builder (always for dynamic lists)
```dart
ListView.builder(
  itemCount: items.length,
  itemExtent: 72.0, // fixed height = massive perf boost
  addRepaintBoundaries: true,
  itemBuilder: (context, index) {
    return ItemTile(item: items[index]);
  },
)
```

### Pagination
```dart
@riverpod
class ServersNotifier extends _$ServersNotifier {
  static const _pageSize = 20;
  int _page = 1;
  bool _hasMore = true;

  @override
  Future<List<Server>> build() async => _fetchPage(1);

  Future<void> loadMore() async {
    if (!_hasMore) return;
    final current = state.valueOrNull ?? [];
    final newItems = await _fetchPage(++_page);
    _hasMore = newItems.length == _pageSize;
    state = AsyncData([...current, ...newItems]);
  }

  Future<List<Server>> _fetchPage(int page) =>
      ref.read(serverRepositoryProvider).getServers(page: page, perPage: _pageSize);
}

// In UI with NotificationListener
NotificationListener<ScrollNotification>(
  onNotification: (notification) {
    if (notification is ScrollEndNotification &&
        notification.metrics.extentAfter < 200) {
      ref.read(serversNotifierProvider.notifier).loadMore();
    }
    return false;
  },
  child: ListView.builder(...),
)
```

---

## Image Optimization

```dart
// Use cached_network_image — never load images without caching
CachedNetworkImage(
  imageUrl: server.flagUrl,
  width: 32,
  height: 32,
  memCacheWidth: 64,  // cache at 2x for retina
  memCacheHeight: 64,
  placeholder: (_, __) => const SizedBox(width: 32, height: 32),
  errorWidget: (_, __, ___) => const Icon(Icons.flag),
)

// For local assets, use flutter_svg for vector flags/icons
SvgPicture.asset('assets/flags/pk.svg', width: 24)
```

---

## RepaintBoundary

```dart
// Wrap complex animated widgets to isolate repaints
RepaintBoundary(
  child: AnimatedConnectionOrb(), // only this repaints during animation
)

// Wrap list items that have animations
ListView.builder(
  itemBuilder: (_, i) => RepaintBoundary(
    child: AnimatedServerTile(server: servers[i]),
  ),
)
```

---

## Compute for Heavy Processing

```dart
// Run expensive operations off the main thread
Future<List<Server>> parseServers(String jsonString) async {
  return compute(_parseServersIsolate, jsonString);
}

List<Server> _parseServersIsolate(String jsonString) {
  // This runs in a background isolate
  final json = jsonDecode(jsonString) as List;
  return json.map((e) => ServerModel.fromJson(e)).toList();
}
```

---

## Memory Management

```dart
// Always dispose controllers
@override
void dispose() {
  _animationController.dispose();
  _textController.dispose();
  _scrollController.dispose();
  _timer?.cancel();
  _subscription?.cancel();
  super.dispose();
}

// With GetX — onClose() instead of dispose
@override
void onClose() {
  _timer?.cancel();
  _subscription?.cancel();
  super.onClose();
}

// With Riverpod — use ref.onDispose
@riverpod
Stream<List<Server>> servers(ServersRef ref) {
  final controller = StreamController<List<Server>>();
  final sub = _startListening(controller);
  ref.onDispose(() {
    sub.cancel();
    controller.close();
  });
  return controller.stream;
}
```

---

## Build Modes & Size Optimization

```bash
# Analyze app size
flutter build apk --release --analyze-size
flutter build appbundle --release

# Split by ABI (smaller downloads)
flutter build apk --release --split-per-abi

# Enable R8/ProGuard
# android/app/build.gradle:
# buildTypes { release { minifyEnabled true; shrinkResources true } }
```

---

## Flutter DevTools Profiling

1. Run in profile mode: `flutter run --profile`
2. Open DevTools: `flutter pub global run devtools`
3. Check **Frame chart** — keep frames under 16ms (60fps)
4. Check **Memory** tab for leaks
5. Use **Widget Inspector** to find unnecessary rebuilds (enable "Highlight repaints")

---

## Performance Checklist

- [ ] All static widgets use `const`
- [ ] `ListView.builder` used for all lists (never `ListView` with `.map`)
- [ ] `itemExtent` set where list item height is fixed
- [ ] `CachedNetworkImage` used for all network images
- [ ] `compute()` used for JSON parsing >1000 items
- [ ] `RepaintBoundary` wraps complex animations
- [ ] All controllers/streams/timers disposed
- [ ] `Obx`/`BlocSelector`/`select` used at smallest widget level
- [ ] No `print()` in release builds
- [ ] Release APK tested with DevTools profiler
