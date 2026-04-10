# UI, Layouts, Theming, Animations & Custom Widgets

## Responsive Design

```dart
// core/utils/responsive.dart
class Responsive {
  static bool isMobile(BuildContext ctx) => MediaQuery.sizeOf(ctx).width < 600;
  static bool isTablet(BuildContext ctx) =>
      MediaQuery.sizeOf(ctx).width >= 600 && MediaQuery.sizeOf(ctx).width < 1200;
  static bool isDesktop(BuildContext ctx) => MediaQuery.sizeOf(ctx).width >= 1200;

  static double w(BuildContext ctx, double percent) =>
      MediaQuery.sizeOf(ctx).width * percent / 100;
  static double h(BuildContext ctx, double percent) =>
      MediaQuery.sizeOf(ctx).height * percent / 100;
}

// ScreenUtil alternative (flutter_screenutil)
// Init in MaterialApp builder:
// ScreenUtil.init(context, designSize: const Size(390, 844));
// Usage: 16.w, 24.h, 14.sp
```

### Adaptive Layout
```dart
class AdaptiveLayout extends StatelessWidget {
  final Widget mobile;
  final Widget? tablet;
  final Widget? desktop;
  const AdaptiveLayout({required this.mobile, this.tablet, this.desktop, super.key});

  @override
  Widget build(BuildContext context) {
    if (Responsive.isDesktop(context)) return desktop ?? tablet ?? mobile;
    if (Responsive.isTablet(context)) return tablet ?? mobile;
    return mobile;
  }
}
```

---

## Theming (Light / Dark / Custom)

```dart
// core/theme/app_theme.dart
class AppTheme {
  static const _primaryColor = Color(0xFF6C63FF);
  static const _secondaryColor = Color(0xFF03DAC6);

  static ThemeData light() => ThemeData(
    useMaterial3: true,
    colorScheme: ColorScheme.fromSeed(
      seedColor: _primaryColor,
      brightness: Brightness.light,
    ),
    textTheme: GoogleFonts.interTextTheme(),
    appBarTheme: const AppBarTheme(centerTitle: true, elevation: 0),
    cardTheme: CardTheme(
      elevation: 2,
      shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(16)),
    ),
    inputDecorationTheme: InputDecorationTheme(
      border: OutlineInputBorder(borderRadius: BorderRadius.circular(12)),
      contentPadding: const EdgeInsets.symmetric(horizontal: 16, vertical: 14),
    ),
    elevatedButtonTheme: ElevatedButtonThemeData(
      style: ElevatedButton.styleFrom(
        minimumSize: const Size(double.infinity, 52),
        shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(14)),
      ),
    ),
  );

  static ThemeData dark() => ThemeData(
    useMaterial3: true,
    colorScheme: ColorScheme.fromSeed(
      seedColor: _primaryColor,
      brightness: Brightness.dark,
    ),
    scaffoldBackgroundColor: const Color(0xFF0D0D0D),
    textTheme: GoogleFonts.interTextTheme(ThemeData.dark().textTheme),
  );
}

// Usage in MaterialApp:
// theme: AppTheme.light(), darkTheme: AppTheme.dark()
// themeMode: ref.watch(themeProvider)
```

---

## Custom Widgets

### Reusable Button
```dart
class AppButton extends StatelessWidget {
  final String label;
  final VoidCallback? onTap;
  final bool isLoading;
  final bool isOutlined;
  final IconData? icon;

  const AppButton({
    required this.label,
    this.onTap,
    this.isLoading = false,
    this.isOutlined = false,
    this.icon,
    super.key,
  });

  @override
  Widget build(BuildContext context) {
    final child = isLoading
        ? const SizedBox(width: 20, height: 20,
            child: CircularProgressIndicator(strokeWidth: 2))
        : Row(
            mainAxisSize: MainAxisSize.min,
            children: [
              if (icon != null) ...[Icon(icon, size: 18), const SizedBox(width: 8)],
              Text(label),
            ],
          );

    return isOutlined
        ? OutlinedButton(onPressed: isLoading ? null : onTap, child: child)
        : ElevatedButton(onPressed: isLoading ? null : onTap, child: child);
  }
}
```

### Shimmer Loading
```dart
// Use shimmer package
class ShimmerCard extends StatelessWidget {
  const ShimmerCard({super.key});

  @override
  Widget build(BuildContext context) {
    return Shimmer.fromColors(
      baseColor: Theme.of(context).colorScheme.surfaceVariant,
      highlightColor: Theme.of(context).colorScheme.surface,
      child: Container(
        height: 80,
        decoration: BoxDecoration(
          color: Colors.white,
          borderRadius: BorderRadius.circular(12),
        ),
      ),
    );
  }
}
```

### App Text Field
```dart
class AppTextField extends StatelessWidget {
  final String label;
  final TextEditingController controller;
  final String? Function(String?)? validator;
  final bool obscureText;
  final TextInputType keyboardType;
  final Widget? suffix;

  const AppTextField({
    required this.label,
    required this.controller,
    this.validator,
    this.obscureText = false,
    this.keyboardType = TextInputType.text,
    this.suffix,
    super.key,
  });

  @override
  Widget build(BuildContext context) {
    return TextFormField(
      controller: controller,
      validator: validator,
      obscureText: obscureText,
      keyboardType: keyboardType,
      decoration: InputDecoration(labelText: label, suffixIcon: suffix),
    );
  }
}
```

---

## Animations

### Implicit Animations
```dart
AnimatedContainer(
  duration: const Duration(milliseconds: 300),
  curve: Curves.easeInOut,
  decoration: BoxDecoration(
    color: isConnected ? Colors.green : Colors.red,
    borderRadius: BorderRadius.circular(isConnected ? 50 : 12),
  ),
)

AnimatedSwitcher(
  duration: const Duration(milliseconds: 250),
  transitionBuilder: (child, anim) => FadeTransition(opacity: anim, child: child),
  child: isLoading
      ? const CircularProgressIndicator(key: ValueKey('loading'))
      : const Icon(Icons.check, key: ValueKey('done')),
)
```

### Explicit Animations (AnimationController)
```dart
class PulseWidget extends StatefulWidget { ... }

class _PulseWidgetState extends State<PulseWidget>
    with SingleTickerProviderStateMixin {
  late final AnimationController _ctrl;
  late final Animation<double> _scale;

  @override
  void initState() {
    super.initState();
    _ctrl = AnimationController(
      vsync: this,
      duration: const Duration(seconds: 1),
    )..repeat(reverse: true);
    _scale = Tween(begin: 1.0, end: 1.08).animate(
      CurvedAnimation(parent: _ctrl, curve: Curves.easeInOut),
    );
  }

  @override
  void dispose() {
    _ctrl.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) =>
      ScaleTransition(scale: _scale, child: widget.child);
}
```

### Page Transitions
```dart
// Custom slide transition
class SlidePageRoute<T> extends PageRouteBuilder<T> {
  final Widget page;
  SlidePageRoute({required this.page})
      : super(
          pageBuilder: (_, __, ___) => page,
          transitionsBuilder: (_, anim, __, child) => SlideTransition(
            position: Tween<Offset>(
              begin: const Offset(1, 0),
              end: Offset.zero,
            ).animate(CurvedAnimation(parent: anim, curve: Curves.easeOut)),
            child: child,
          ),
          transitionDuration: const Duration(milliseconds: 300),
        );
}
```

---

## Layout Best Practices

- Always use `const` constructors for stateless widgets
- Use `SizedBox` instead of `Container` for spacing/sizing only
- Prefer `ListView.builder` over `ListView` for dynamic content
- Use `Expanded` / `Flexible` inside `Row`/`Column` instead of fixed sizes
- Avoid deep widget nesting — extract into named widgets or methods
- Use `RepaintBoundary` around independently animating children
- Use `AutomaticKeepAliveClientMixin` to preserve page state in `TabView`/`PageView`
