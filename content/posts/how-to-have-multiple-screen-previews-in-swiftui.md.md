---
title: How to Have Multiple Screen Previews in Swiftui
date: 2020-04-06T12:39:36.964Z
categories:
  - little-bites
tags:
  - swift
  - xcode
  - swiftui
comments: true
---
Today I learned that you can actually create multiple Xcode screen previews in SwiftUI.

Assuming you have a SwiftUI `View` named `ContentView`. In the `PreviewProvider`, create a `Group` and init multiple childs `ContentView()` inside it. For example:

```
struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        Group {
            ContentView()
                .previewDevice(PreviewDevice(rawValue: "iPhone 11"))
                .previewDisplayName("iPhone 11") // Optional
            ContentView()
                .previewDevice(PreviewDevice(rawValue: "iPhone 8"))
                .previewDisplayName("iPhone 8 Dark")
                .environment(\.colorScheme, .dark)
                .environment(\.sizeCategory, .accessibilityLarge)
            ContentView()
                .previewDevice(PreviewDevice(rawValue: "iPhone SE"))
                .previewDisplayName("iPhone SE")
        }

    }
}
```

 Here's the above code in action

![Xcode 11 Multiple Previews](/images/uploads/preview.gif)

This is going to be super useful when you want to quickly preview your `View` in different screen sizes, accessibility mode or color schemes. Neat huh?

References:
- [Hacking With Swift - SwiftUI tips and tricks](https://www.hackingwithswift.com/quick-start/swiftui/swiftui-tips-and-tricks)