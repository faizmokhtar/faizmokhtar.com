---
title: How to use SwiftUI in UIKit Project
date: 2020-04-04T10:09:30.345Z
categories:
  - little-bites
tags:
  - swift
  - xcode
comments: true
---
Did you know that SwiftUI `View` can be use in UIKit project? Everything is a `View` in SwiftUI, so for it to work as `UIViewController` you have to make use of `UIHostingController`.

Assuming you have a SwiftUI `View` named `SwiftUIView` like so:

```
let swiftUIView = SwiftUIView()
```

## Initializing it programmatically

To initialize it programmatically, set the SwiftUI `View` as the `rootView` of the `UIHostingController`

```
let vc = UIHostingController(rootView: ContentView())
self.present(vc, animated: true, completion: nil)
```

## Initializing it in Storyboard

To initialize it in Storyboard:

1. Add a Hosting View Controller and create a segue to it

   ![Search for UIHostingController](/images/uploads/uihosting-storyboard.png "Search for UIHostingController in Storyboard")
2. Create an `IBSegueAction` where you can init the `UIHostingController` like so

```
 @IBSegueAction func openSwiftUIView(_ coder: NSCoder) -> UIViewController? {
     return UIHostingController(coder: coder, rootView: swiftUIView))
 }
```

##### References:

1. [Apple documentation on UIHostingController](https://developer.apple.com/documentation/swiftui/uihostingcontroller)