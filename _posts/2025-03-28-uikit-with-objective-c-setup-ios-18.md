---
layout: post
title: 'Programmatic UIKit with ObjC in iOS 18'
date: 2025-03-28 18:21:33 -0500
categories: [UIKit, ObjC]
tag: [ios]
# media_subpath: https://eacardenase.github.io
---

Hi there! Most probably you will be thinking, why would I need to setup a new iOS project using UIKit when there is SwiftUI, and most of all, configured with Objective-C!

Well, the thing is that UIKit is far from dead, and there's a high chance you will encounter ObjC in the wild. Or you just wanna learn something new. Here, we are gonna setup a pretty basic UIKit project built from scratch with ObjC that will just show a `UIViewController`'s view background set to blue, using programmatic-ui instead of the default storyboard setup.

Go ahead and create a new project on XCode. Select _iOS_, App template, pick _Storyboard_ as interface and good old _Objective-C_ as language.

> The project would look something like the following image

![](/assets/img/objc-setup-1.png)

Build and run the project to check that everything works.

Now that everything is setup, we need to get rid of that dreaded `Main.storyboard` and setup our application to use programmatic UIKit.

Delete and move to the trash `Main.storyboard`.

With our `Main.storyboard` gone, it's time to also remove its references within the project.

Select the project and go to the **_Build Settings_**. Under the Info.list Values section, select and delete the property named _UIKit Main Storyboard File Base Name_, just like shown in the following image:

![](/assets/img/objc-setup-2.png)

Next, we're going to remove the reference to `Main.storyboard` from our Scene Configuration. Go to the **_Info_** tab just to the left of the previous **_Build Settings_** tab.

Under the _Application Scene Manifest > Scene Configuration > Window Application Session Role > Item 0 (Default Configuration)_, select and delete the _Storyboard Name_ property, as shown in the following image:

![](/assets/img/objc-setup-3.png)

Now that the `Main.storyboard` references are gone, it's time to setup our programmatic UIKit setup.

Let's start by setting the `backgroundColor` of our default _ViewController_'s view to `UIColor.cyanColor` within the `viewDidLoad` method. This will give us a visual guide and help us make sure that our changes work.

```objc
//  ViewController.m

- (void)viewDidLoad {
    [super viewDidLoad];

    self.view.backgroundColor = UIColor.cyanColor;
}
```

Next, we're going to update our `SceneDelage` `scene:willConnectToSession:options` method in order to set our an instance of our `ViewController` as the window's `rootViewController`.

```objc
// SceneDelegate.m

// Don't forget to import the header at the top of the file
#import "ViewController.h"

- (void)scene:(UIScene *)scene willConnectToSession:(UISceneSession *)session options:(UISceneConnectionOptions *)connectionOptions {
    self.window = [[UIWindow alloc] initWithWindowScene:(UIWindowScene *)scene];
    self.window.rootViewController = [[ViewController alloc] init];

    [self.window makeKeyAndVisible];
}
```

We just finished. Go ahead and run the project, you should see our beautiful displayed `ViewController`'s cyan background in the simulator.

![](/assets/img/objc-setup-4.png){: width="350" style="display: block; margin: auto" }
