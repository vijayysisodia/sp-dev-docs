---
title: Set up your Microsoft 365 tenant
description: Build and deploy client-side web parts using the SharePoint Framework by setting up a Microsoft 365 tenant.
ms.date: 02/26/2021
ms.prod: sharepoint
ms.localizationpriority: high
ms.custom: scenarios:getting-started
---

# Set up your Microsoft 365 tenant

To build and deploy client-side web parts using the SharePoint Framework, you need a Microsoft 365 tenant.

If you already have a Microsoft 365 tenant, see the section [Create app catalog site](#create-app-catalog-site).

If you don't have one, you can get a Microsoft 365 developer subscription when you join the [Microsoft 365 Developer Program](https://developer.microsoft.com/office/dev-program). See the [Microsoft 365 Developer Program documentation](/office/developer-program/office-365-developer-program) for step-by-step instructions about how to join the Microsoft 365 Developer Program and sign up and configure your subscription.

> [!NOTE]
> Make sure that you are signed out of any existing Microsoft 365 tenants before you sign up for the Microsoft 365 Developer Program.

You can also follow these steps by watching this video on the SharePoint PnP YouTube Channel:

> [!Video https://www.youtube.com/embed/yc1IYgYp7qQ]

## Create app catalog site

You need an app catalog to upload and deploy web parts. If you've already set up an app catalog, see [Create app catalog sites](#create-app-catalog-site).

### To create an app catalog site

1. Go to the **SharePoint Admin Center** by entering the following URL in your browser. Replace **yourtenantprefix** with your Microsoft 365 tenant prefix.

    Commercial Tenant
    
    ```http
    https://{your-tenant-prefix}-admin.sharepoint.com
    ```
    
    GCC High Tenant
    
    ```http
    https://{your-tenant-prefix}-admin.sharepoint.us
    ```

1. In the left sidebar, select **More features**
1. Locate the section **Apps** and select **Open**.
1. On the **Apps** page, select **App Catalog**.
1. Select **OK** to create a new app catalog site.
1. On the next page, enter the following details:

    - **Title**: Enter **app catalog**.
    - **Web Site Address _suffix_**: Enter your preferred suffix for the app catalog; for example: **apps**.
    - **Administrator**: Enter your username, and then select the **resolve** button to resolve the username.

1. Select **OK** to create the app catalog site.

SharePoint creates the app catalog site, and you can see its progress in the SharePoint admin center.

## Create a new site collection

You also need a site collection and a site for your testing. You can create a new site collection by using any of the available templates.

1. Navigate to **SharePoint Admin Center** by entering the following URL in your browser. Replace **{your-tenant-prefix}** with your Microsoft 365 tenant prefix:

    Commercial Tenant
    
    ```http
    https://{your-tenant-prefix}-admin.sharepoint.com
    ```

    GCC High Tenant
    
    ```http
    https://{your-tenant-prefix}-admin.sharepoint.us
    ```

1. In the left sidebar, select **Sites > Active sites**.
1. Select **Create** from the toolbar at the top of the page.
1. On the **Create a site** page, select **Team site**.
1. In the panel that appears, enter required details to create the site (*name, owner, and language*):
1. Select **Next** to create the site collection.

After SharePoint creates the site, you can browse to your site collection by selecting **Finish** & entering the URL of the new site.

> [!NOTE]
> In this case, we are creating a new group associated team site with modern user interface experience. You could just as well create a *communication site* to be used as your test site collection supporting your development.

> [!NOTE]
> You can potentially use same tenant for developing SharePoint Framework experiences, especially for initial development experiences. We do however recommend to use isolated developer tenants for each of the developers for best isolated developer experience.

## SharePoint Workbench

SharePoint Workbench is a developer design surface that enables you to quickly preview and test web parts without deploying them in SharePoint. SharePoint Framework developer toolchain contains a version of the Workbench that works locally and helps you quickly test and validate solutions that you're building.

It's also hosted in your tenant to preview and test your local web parts in development. You can access the **Hosted SharePoint Workbench** from any SharePoint site in your tenancy by browsing to the following URL:

```http
https://your-sharepoint-site/_layouts/workbench.aspx
```

## Next steps

Now that you've configured your SharePoint tenant, [set up your development environment](./set-up-your-development-environment.md) to build client-side web parts.
