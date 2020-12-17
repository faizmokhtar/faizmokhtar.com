---
title: 'How to fix Xcode: "Could Not Locate Device Support Files" error'
date: 2020-05-27T04:43:29.783Z
categories:
  - little-bites
tags:
  - xcode
  - tools
comments: true
---
There may be a time when you try to run your app in your device and you get the following error:

> **Could not locate device support files.**
>
> This iPhone (Model ...) is running iOS 13.4 (11E608c), which may not be supported by this version of Xcode.

This issue usually happened when you are still developing your app using old version of Xcode but your device have already been upgraded to latest iOS version that is not supported by Xcode. 

There are multiple ways to solve this issue:

1. **Upgrade your Xcode to the latest version** - While this is the most obvious way to fix the issue, it could be your most hardest too. Depending on the situation, you might have to update all your projects issues before upgrading (Unsupported swift version, Unsupported SDK version, etc). That's a lot of work
2. **Keep two versions of Xcode installed** - This have been my preferred option whenever there's a new iOS beta version dropped and I couldn't wait to upgrade my device (living on the edge baby!). You have to symlink the `DeviceSupport/` folder from the beta or latest version to the stable version that you've been using.[^1] However this option might not be feasible if you have a limited disk space on your machine.
3. **Copying the latest device support files to `DeviceSupport` folder** - I just discovered this today and still in awe on how simple it is. I will list the steps down below.

## To fix "Could Not Locate Device Support Files" Error Issue with new device support file

1. Go to the following Github repo: [iGhibli/iOS-DeviceSupport](https://github.com/iGhibli/iOS-DeviceSupport/tree/master/DeviceSupport)
2. Find the zip files that's matching your device's iOS version and download it.
3. Open the following path in Finder:

   ```bash
   $~ open /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/DeviceSupport/
   ```
4. Copy and paste the zip files that you have downloaded to `DeviceSupport/` folder
5. Close and restart your Xcode.

That's it. You should be able to run your app in your device now. Hope you will find this tips useful. 

Until next time. ✌️

[^1]: [@steipete](https://twitter.com/steipete) did an awesome job of maintaining a [gist of the command](https://gist.github.com/steipete/d9b44d8e9f341e81414e86d7ff8fb62d) to refer too.

## References:

1. [github.com/iGhibli/iOS-DeviceSupport](https://github.com/iGhibli/iOS-DeviceSupport)
2. [StackOverflow - Could not locate device support files in Xcode](https://stackoverflow.com/questions/54624850/could-not-locate-device-support-files-in-xcode)