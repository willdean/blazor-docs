---
title: Server-side Blazor
page_title: First Steps with Server-side UI for Blazor
description: First Steps with UI for Blazor Server-side
slug: getting-started/server-side
tags: get,started,first,steps,server
published: true
position: 2
---

# First Steps with Server-side UI for Blazor

This article explains how to get the Telerik UI for Blazor components in your **Server-side** Blazor project and start using them quickly. The process consists of the following steps:

1. [Set Up a Blazor Project](#set-up-a-blazor-project)
1. [Add the Telerik NuGet Feed to Visual Studio](#add-the-telerik-nuget-feed-to-visual-studio)
1. [Add the Telerik Components to Your Project](#add-the-telerik-components-to-your-project)
     * [Add to an Existing Project](#add-to-existing-project)
1. [Add a Telerik Component to a View](#add-a-telerik-component-to-a-view)

@[template](/_contentTemplates/common/get-started.md#add-latest-ms-bits-server-side-link)


@[template](/_contentTemplates/common/get-started.md#add-nuget-feed)


## Add the Telerik Components to Your Project

To use Blazor server-side, you need to use the `Blazor App` type of project with its `Blazor Server App` flavor.
@[template](/_contentTemplates/common/get-started.md#project-creation-part-1)

1. Choose the `Blazor Server App` project type and click `Create`.

    ![Select Blazor Project Type](images/choose-project-template-server-blazor.png)


### Add to Existing Project

@[template](/_contentTemplates/common/get-started.md#get-access)

    1. Right-click on the project in the solution and select `Manage NuGet Packages`:
    
       ![](images/manage-nuget-packages-for-server-app.png)
    
    1. Choose the `telerik.com` feed, find the **`Telerik.UI.for.Blazor`** package and click `Install` (make sure to use the latest version). If you don't have a commercial license, you will only see `Telerik.UI.for.Blazor.Trial`. Use that instead.
    
         ![Add Telerik Blazor Package to the project](images/add-telerik-nuget-to-server-app.png)

        
1. Open the `~/Pages/_Host.cshtml` and register the [Theme stylesheet]({%slug general-information/themes%}) (note the escaping for the `@` symbol):

    **HTML**
    
        <link rel="stylesheet" href="https://unpkg.com/@@progress/kendo-theme-default@@latest/dist/all.css" />
        
1. Remove the contents of the `<app></app>` element (see [this issue](https://feedback.telerik.com/blazor/1425656-using-renderstaticcomponentasync-breaks-telerik-components)).
        
1. @[template](/_contentTemplates/common/js-interop-file.md#add-js-interop-file-to-getting-started-server)
        
1. Open the `~/Startup.cs` file in the and register the Telerik Blazor service:

    **C#**
    
        namespace MyBlazorAppName
        {
            public class Startup
            {
                public void ConfigureServices(IServiceCollection services)
                {
                    //more code may be present here
                    services.AddTelerikBlazor();
                }
                
                //more code may be present here
            }
        }

1. @[template](/_contentTemplates/common/get-started.md#telerik-main-container-text)

    **MainLayout.razor**
    
        @[template](/_contentTemplates/common/get-started.md#telerik-main-container-snippet)


    
Now your project can use the Telerik UI for Blazor components.

## Add a Telerik Component to a View

The final step is to actually use a component on a view and run it in the browser. For example:

1. **Add** a **Button** component to the `~/Components/Pages/Index.cshtml` view:
@[template](/_contentTemplates/common/get-started.md#add-component-sample)

## See Also

* [Get Started with Client-side Blazor]({%slug getting-started/client-side%})
* [Telerik Private NuGet Feed]({%slug installation/nuget%})
* [Getting Started Videos for Blazor](https://www.youtube.com/watch?v=aaRAZYaJ4xc&list=PLvmaC-XMqeBYPTwcm478vs8Rujq2tiVJo)

