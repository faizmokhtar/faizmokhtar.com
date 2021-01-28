---
title: Exploring Tuist - A First Look (Part 1)
date: 2021-01-28T04:49:34.404Z
tags:
  - exploration
  - tools
  - xcode
comments: true
---
Today I'm exploring [Tuist - A project generation tools for Xcode projects][1]. It's a tool similar to [Xcodegen][2] or if you have a background in backend programming, you can see it as an[Infrastructure as Code][3] tool.

One of the biggest selling points of this project aside from not having to deal with the dreaded `.xcodeproj` conflicts is that it uses Swift. I feel like it will help your team to easily adopt it.

This blog post is just to document my process of learning [Tuist][1]. I have no prior experience using it in a personal or team settings.

## Installation

The installation process is seamless and fast. I only have to run the following command to set `tuist` up.

```
$~ bash <(curl -Ls https://install.tuist.io)

```

## Project generation

Following the docs, I set up my first project. I need to create an empty directory first and run the following command:

```
tuist init --platform ios

```

This will bootstrap files necessary to create an iOS application. Running `tree`, it will show the following directory structure

````
.
├── Project.swift
├── Targets
│   ├── TuistApp
│   │   ├── Resources
│   │   │   └── LaunchScreen.storyboard
│   │   ├── Sources
│   │   │   └── AppDelegate.swift
│   │   └── Tests
│   │       └── AppTests.swift
│   ├── TuistAppKit
│   │   ├── Sources
│   │   │   └── TuistAppKit.swift
│   │   └── Tests
│   │       └── TuistAppKitTests.swift
│   └── TuistAppUI
│       ├── Sources
│       │   └── TuistAppUI.swift
│       └── Tests
│           └── TuistAppUITests.swift
└── Tuist
    ├── Config.swift
    └── ProjectDescriptionHelpers
        └── Project+Templates.swift

13 directories, 10 files
````

`Project.swift` is where I have to define your project descriptions. Right now, I still can't run the project yet. To do that, I need to run the following commands.

```
$~ tuist generate

```

This will generate the `.xcodeproj`, `.xcworkspace`, and `Derived/` files necessary to run the project.

````
.
├── Derived
│   ├── InfoPlists
│   │   ├── TuistApp.plist
│   │   ├── TuistAppKit.plist
│   │   ├── TuistAppKitTests.plist
│   │   ├── TuistAppTests.plist
│   │   ├── TuistAppUI.plist
│   │   └── TuistAppUITests.plist
│   └── Sources
│       └── Bundle+TuistApp.swift
├── Project.swift
├── Targets
│   ├── TuistApp
│   │   ├── Resources
│   │   │   └── LaunchScreen.storyboard
│   │   ├── Sources
│   │   │   └── AppDelegate.swift
│   │   └── Tests
│   │       └── AppTests.swift
│   ├── TuistAppKit
│   │   ├── Sources
│   │   │   └── TuistAppKit.swift
│   │   └── Tests
│   │       └── TuistAppKitTests.swift
│   └── TuistAppUI
│       ├── Sources
│       │   └── TuistAppUI.swift
│       └── Tests
│           └── TuistAppUITests.swift
├── Tuist
│   ├── Config.swift
│   └── ProjectDescriptionHelpers
│       └── Project+Templates.swift
├── TuistApp.xcodeproj
│   ├── project.pbxproj
│   ├── project.xcworkspace
│   │   └── contents.xcworkspacedata
│   └── xcshareddata
│       ├── xcdebugger
│       └── xcschemes
│           ├── TuistApp.xcscheme
│           ├── TuistAppKit.xcscheme
│           ├── TuistAppKitTests.xcscheme
│           ├── TuistAppTests.xcscheme
│           ├── TuistAppUI.xcscheme
│           └── TuistAppUITests.xcscheme
└── TuistApp.xcworkspace
    ├── contents.xcworkspacedata
    └── xcshareddata
        └── xcschemes
            └── TuistApp-Project.xcscheme

24 directories, 27 files
````

However, right now I couldn't figure out why the projects are structured the way it(ie. `TuistApp/`, `TuistAppKit`, `TuistAppUI`. I feel like maybe it has something to do with [µFeatures Architecture][4] define in the docs. I tried to customize the project description following the examples given but it doesn't exactly generate new files like the initial setup either. Maybe I need to use `tuist scaffold` for that.

I feel like the best way to figure out how to use it is by migrating an existing project that I have to use [Tuist][1]. So until then, here's a helpful command that I think will help you to figure out how it works.

```
$~ tuist --help
```

Bye 😆

[1]: https://tuist.io/
[2]: https://github.com/yonaskolb/XcodeGen
[3]: https://en.wikipedia.org/wiki/Infrastructure_as_code
[4]: https://tuist.io/docs/building-at-scale/microfeatures/