---
title: Setting up UIKit programmatically with Objective-C
description: UIKit project set up with Objective-C and Programmatic UI in iOS 18.
date: 2025-03-28 18:21:33 -0500
categories: [UIKit, Objective-C]
tag: [ios, uikit]
mermaid: true
---

Hi there! In this post we're going to start a small ToDo app programmatically using UIKit written in Objective-C.

```mermaid
---
title: Entity Relationships
---
erDiagram
    Item }o--|| Asset-Type: Item
    Item {
        string item_key PK
        string item_name
        string serial_number
        int value_in_dollars
    }
    Asset-Type {
        string label
    }
```
