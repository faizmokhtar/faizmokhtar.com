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
Did you know that SwiftUI can be use in UIKit project? To use SwiftUI in UIKit project, you have to make use of `UIHostingViewController`. `UIHostingViewController` is a `UIViewController` that "host" a SwiftUI view. Get it? 😉

Assuming you have a SwiftUI `View` named `SwiftUIView` like so:

```
let swiftUIView = SwiftUIView()
```

## Initializing it programmatically

To initialize it programmatically, set the SwiftUI `View` as the `rootView` of the `UIHostingController`.

```
let vc = UIHostingController(rootView: swiftUIView)
self.present(vc, animated: true, completion: nil)
```

## Initializing it in Storyboard

Using it in Storyboard requires a little bit more work.

1. First, add a Hosting View Controller and create a segue to it

   ![Search for UIHostingController](/images/uploads/uihosting-storyboard.png "Search for UIHostingController in Storyboard")

2. Then, create an `IBSegueAction` where you can init the `UIHostingController` like so

```
 @IBSegueAction func openSwiftUIView(_ coder: NSCoder) -> UIViewController? {
     return UIHostingController(coder: coder, rootView: swiftUIView))
 }
```

That's it.

##### References:

1. [Apple documentation on UIHostingController](https://developer.apple.com/documentation/swiftui/uihostingcontroller)