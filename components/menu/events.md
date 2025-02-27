---
title: Events
page_title: Menu for Blazor | Events
description: Events in the Menu for Blazor
slug: components/menu/events
tags: telerik,blazor,menu,events
published: true
position: 20
---

# Events

This article explains the events available in the Telerik Menu for Blazor:

* [OnClick](#onclick)

## OnClick

The `OnClick` event fires when the user clicks or taps on a menu item. It receives the model of the item as an argument that you can cast to the concrete model type you are using.

You can use the `OnClick` event to react to user choices in a menu without using navigation to load new content automatically.

>caption Handle OnClick

````CSHTML
@using Telerik.Blazor.Components.Menu

<TelerikMenu Data="@MenuItems" OnClick="@((MenuItem item) => OnClickHandler(item))">
</TelerikMenu>

Last clicked item: @ClickedItem?.Text

@code {
    public MenuItem ClickedItem { get; set; }

    protected void OnClickHandler(MenuItem item)
    {
        ClickedItem = item;
    }

    public List<MenuItem> MenuItems { get; set; }

    public class MenuItem
    {
        public string Text { get; set; }
        public string Icon { get; set; }
        public List<MenuItem> Items { get; set; }
    }

    protected override void OnInitialized()
    {
        MenuItems = new List<MenuItem>()
        {
            new MenuItem()
            {
                Text = "Share",
                Icon = "k-i-share",
                Items = new List<MenuItem>()
            {
                    new MenuItem()
                    {
                        Text = "FaceBook",
                        Icon = "k-i-facebook"
                    },
                    new MenuItem()
                    {
                        Text = "LinkedIn",
                        Icon = "k-i-linkedin"
                    },
                    new MenuItem()
                    {
                        Text = "Twitter",
                        Icon = "k-i-twitter"
                    },
                }
            },
            new MenuItem()
            {
                Text = "Map Location",
                Icon = "k-i-marker-pin"
            }
        };

        base.OnInitialized();
    }
}
````


## See Also

* [Templates]({%slug components/menu/templates%})
