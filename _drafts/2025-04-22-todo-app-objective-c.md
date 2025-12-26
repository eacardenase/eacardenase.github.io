---
title: ToDo app with UIKit, programmatic UI and Objective-C
description: ToDO app built with UIKit and Objective-C in iOS 18.
date: 2025-04-22 18:21:33 -0500
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
