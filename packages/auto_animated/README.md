# Auto animated

Auto animated widgets for flutter 

Animate on scroll containers:
- `AutoAnimatedList`
- `AutoAnimatedSliverList`
- `AutoAnimatedGrid`
- `AutoAnimatedSliverGrid`
- `AnimateOnVisibilityChange`

Another animated widgets
- `AutoAnimatedIconButton`

## Showcase

| ListView                  | GridView                   | Sliver                       |
| ---                       | ---                        | ---                          |
|![](https://raw.githubusercontent.com/rbcprolabs/packages.flutter/master/packages/auto_animated/example/media/2.0/list.gif?raw=true)  | ![](https://raw.githubusercontent.com/rbcprolabs/packages.flutter/master/packages/auto_animated/example/media/2.0/grid.gif?raw=true)  | ![](https://raw.githubusercontent.com/rbcprolabs/packages.flutter/master/packages/auto_animated/example/media/2.0/sliver.gif?raw=true)  |

## Getting Started
In your flutter project add the dependency:

[![pub package](https://img.shields.io/pub/v/auto_animated.svg)](https://pub.dartlang.org/packages/auto_animated)

```yaml
dependencies:
  ...
  auto_animated: any
```
For help getting started with Flutter, view the online [documentation](https://flutter.io/).

## `AutoAnimatedList` usage example
### Make an automatically animated list in 2 minutes? Easily!

```dart
AutoAnimatedList(
    // Start animation after (default zero)
    delay: Duration(seconds: 1),
    // Show each item through
    showItemInterval: Duration(milliseconds: 500),
    // Animation duration
    showItemDuration: Duration(seconds: 1),
    // Other properties correspond to the `ListView` widget
    scrollDirection: Axis.horizontal,
    itemsCount: 10,
    itemBuilder: _buildAnimatedItem,
)

// Build item
Widget _buildAnimatedItem(
    BuildContext context,
    int index,
    Animation<double> animation,
) =>
    // Wrap with fade transition
    FadeTransition(
        opacity: Tween<double>(
            begin: 0,
            end: 1,
        ).animate(animation),
        // And slide transition
        child: SlideTransition(
            position: Tween<Offset>(
                begin: Offset(0, -0.1),
                end: Offset.zero,
            ).animate(animation),
            // Paste you Widget
            child: YouWidgetHere(title: index.toString()),
        ),
    )
```

## `AutoAnimatedSliverGrid` usage example

```dart
AutoAnimatedSliverGrid(
  delay: Duration(milliseconds: 500) * 4,
  showItemInterval: Duration(milliseconds: 500),
  showItemDuration: Duration(seconds: 1),
  itemCount: 6,
  itemBuilder: animationItemBuilder(
    (index) => YouWidgetHere(title: index.toString()),
  ),
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
    crossAxisCount: 3,
  ),
)
```

## `AutoAnimatedIconButton` usage example
### Basic
```dart
AutoAnimatedIconButton(
    icon: AnimatedIcons.arrow_menu,
    onPressed: () {},
)
```
### With separate tooltips
```dart
AutoAnimatedIconButton(
    icon: AnimatedIcons.arrow_menu,
    firstTooltip: 'Event',
    secondTooltip: 'Add',
)
```