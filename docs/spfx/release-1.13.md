---
title: SharePoint Framework v1.13 release notes
description: Release notes for the SharePoint Framework v1.13 release
ms.date: 09/08/2021
ms.prod: sharepoint
ms.localizationpriority: high
---
# SharePoint Framework v1.13 release notes

We will be releasing multiple public beta builds using the **@next** tag in the [NPMJS.org](https://www.npmjs.org) registry before final release candidates and a final public release.

[!INCLUDE [spfx-release-beta](../../includes/snippets/spfx-release-beta.md)]

- beta.17 **Released:** August 22, 2021
- beta.15 **Released:** July 22, 2021

[!INCLUDE [spfx-release-notes-common](../../includes/snippets/spfx-release-notes-common.md)]

## Install the latest beta release

Install the latest beta release of the SharePoint Framework (SPFx) by including the **@next** tag:

```console
npm install @microsoft/generator-sharepoint@next --global
```

## Upgrading projects from v1.12.1 to v1.13

1. In the project's **package.json** file, identify all SPFx v1.12.1 packages. For each SPFx package:
    1. Uninstall the existing v1.12.1 package:

        ```console
        npm uninstall @microsoft/{spfx-package-name}@1.12.1
        ```

    1. Install the refreshed v1.13 {version-release} package:

        ```console
        npm install @microsoft/{spfx-package-name}@next --save --save-exact
        ```

[!INCLUDE [spfx-release-upgrade-tip](../../includes/snippets/spfx-release-upgrade-tip.md)]

## New features and capabilities

- The biggest new feature of this release is the extensibility model for the upcoming Viva Connections feature. The beta will allow you to create Adaptive Card Extensions (ACEs) and test them in the hosted workbench.
  - *See [Overview of Viva Connections Extensibility](viva/overview-viva-connections.md) for more details.*
- Update the Microsoft Teams SDK to v1.10.

> [!NOTE]
> The extensibility model for the upcoming Viva Connections feature is currently rolling out in production and might not be available across all tenants yet. If you want to immediately start working with ACEs you can do that by creating a link to the workbench (for example `https://contoso.sharepoint.com/_layouts/15/workbench.aspx`) in a navigation node in a modern page. Then use that node to access the workbench.

## Deprecations and removed items in this release

- **Local workbench removed**: This release will also mark the removal of the local workbench, as well as the removal of the on-prem questions in the Yeoman generator. On-prem is still supported, and the SPFx v1.12.1 Yeoman generator, as well as previous versions, continue to generate on-prem solutions. The hosted workbench is now the way to test your code.

    To configure the browser launch correctly, update the `initialPage` property within the **./config/serve.json** to point to your SharePoint Online tenant. For example: `https://contoso.sharepoint.com/_layouts/15/workbench.aspx`.

    Not performing this configuration task will result in an error the first time `gulp serve` runs.
