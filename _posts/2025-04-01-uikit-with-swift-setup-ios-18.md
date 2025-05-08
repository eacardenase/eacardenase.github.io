---
title: Setting up UIKit programmatically with Swift
description: UIKit project set up with Swift and Programmatic UI in iOS 18.
date: 2025-04-01 19:39:55 -0500
categories: [UIKit, Swift]
tag: [ios, uikit, swift]
---

Hi there! Most probably you will be thinking, why would I need to setup a new iOS project using UIKit when there is SwiftUI already?

Well, the thing is that UIKit is far from dead, and there's a high chance you will encounter it in the wild. Here, we are gonna setup a pretty basic UIKit project built from scratch with Swift that will just show a `UIViewController`'s view background set to blue, using programmatic-ui instead of the default storyboard setup.

> You can see a similar setup using Objective-C on [this post]({% post_url 2025-03-28-uikit-with-objective-c-setup-ios-18 %}){: target="_blank" }.

## Project set up

Go ahead and create a new project on XCode. Select _iOS_, App template, pick _Storyboard_ as interface and _Swift_ as programming language.

> The project set up would look something like this
{: .prompt-info }

![XCode Project](/assets/img/swift-setup-1.png)

Build and run the project to check that everything works.

## Storyboards cleanup

Now that everything is setup, we need to get rid of that dreaded `Main.storyboard` and setup our application to use programmatic UIKit.

Delete and move to the trash `Main.storyboard`.

With our `Main.storyboard` gone, it's time to also remove its references within the project.

Select the project and go to the **_Build Settings_**. Under the Info.plist Values section, select and delete the property named _UIKit Main Storyboard File Base Name_, just like shown in the following image:

![XCode Project](assets/img/swift-setup-2.png)

Next, we're going to remove the reference to `Main.storyboard` from our Scene Configuration. Go to the **_Info_** tab just to the left of the previous **_Build Settings_** tab.

Under the _Application Scene Manifest > Scene Configuration > Window Application Session Role > Item 0 (Default Configuration)_, select and delete the _Storyboard Name_ property, as shown in the following image:

![XCode Project](/assets/img/swift-setup-3.png)

## Programmatic-UI set up

Now that the `Main.storyboard` references are gone, it's time to setup our programmatic UIKit setup.

Let's start by setting the `backgroundColor` of our default _ViewController_'s view to `UIColor.systemPurple` within the `viewDidLoad` method. This will give us a visual guide and help us make sure that our changes work.

```swift
override func viewDidLoad() {
    super.viewDidLoad()
    
    view.backgroundColor = .systemPurple
}
```
{: file="ViewController.swift" }

Next, we're going to update our `SceneDelage` `scene:willConnectToSession:options` method in order to set our an instance of our `ViewController` as the window's `rootViewController`.

```swift
func scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions) {
    guard let scene = (scene as? UIWindowScene) else { return }
    
    window = UIWindow(windowScene: scene)
    window?.makeKeyAndVisible()
    window?.rootViewController = ViewController()
}
```
{: file="SceneDelegate.swift" }

We just finished. Go ahead and run the project, you should see our beautiful displayed `ViewController`'s purple background in the simulator.

![Simulator](/assets/img/swift-setup-4.png){: width="350" }
_UIViewController's background color set to UIColor.systemPurple_

If you want to take a deeper look, here's the [GitHub repository](https://github.com/eacardenase/objc-programmatic-uikit){: target="_blank" } with everything we have covered so far.
