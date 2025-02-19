---
title: Work with __REQUESTDIGEST
description: Add a valid request digest to your request when executing non-GET REST requests to the SharePoint API.
ms.date: 06/29/2020
ms.prod: sharepoint
ms.localizationpriority: high
---
# Work with __REQUESTDIGEST

When executing non-GET REST requests to the SharePoint REST API, you must include a valid request digest to your request. The digest proves validity of your request to SharePoint. Because this token is valid only for a limited period of time, you must ensure the token is valid before adding it to your request or the request fails.

In classic pages, SharePoint includes a request digest token on the page in a hidden field named **__REQUESTDIGEST**. One of the most common approaches to work with the request digest is to obtain it from that field and add it to the request, for example:

```javascript
var digest = $('#__REQUESTDIGEST').val();
$.ajax({
  url: '/_api/web/...'
  method: "POST",
  headers: {
    "Accept": "application/json; odata=nometadata",
    "X-RequestDigest": digest
  },
  success: function (data) {
    // ...
  },
  error: function (data, errorCode, errorMessage) {
    // ...
  }
});
```

Such a request would work initially, but if the user has the page open for a longer period of time, the request digest on the page expires and the request fails with an HTTP 403: FORBIDDEN** result. By default, a request digest token is valid for 30 minutes, so before using it, you must ensure that it's still valid. In the past you had to do this manually, by comparing the timestamp from the request digest with the current time.

The SharePoint Framework (SPFx) simplifies this process by offering you two ways of ensuring that your request has a valid request digest token.

## Use the SPHttpClient to communicate with the SharePoint REST API

The recommended way to communicate with the SharePoint REST API is to use the **SPHttpClient** API included in SPFx. This class wraps issuing REST requests to the SharePoint REST API with convenient logic that simplifies your code.

For example, whenever you issue a non-GET request with the **SPHttpClient** API, it automatically obtains a valid request digest and adds it to the request. This significantly simplifies your solution because you don't need to build code to manage request digest tokens and ensure their validity.

If you're building new customizations on the SharePoint Framework, you should always use the **SPHttpClient** API to communicate with the SharePoint REST API.

Sometimes you can't use the **SPHttpClient** API. For example, when you're migrating an existing customization to the SharePoint Framework and want to keep as much of the original code as possible, or you're building a customization by using a library such as AngularJS that has its own services for issuing web requests.

## Retrieve a valid request digest by using the DigestCache service

If you can't use the **SPHttpClient** API for communicating with the SharePoint REST API, you can obtain a valid request digest token by using the **DigestCache** service provided with the SharePoint Framework.

The benefit of using the **DigestCache** service over manually obtaining a valid request digest token is that the **DigestCache** automatically checks if the previously retrieved request digest is still valid. If it's expired, the **DigestCache** service automatically requests a new request digest token from SharePoint and stores it fro later requests. Using the **DigestCache** simplifies your code and makes your solution more robust.

### To use the DigestCache service in your code

1. Import the **DigestCache** and **IDigestCache** types from the **\@microsoft/sp-http** package:

    ```typescript
    // ...
    import { IDigestCache, DigestCache } from '@microsoft/sp-http';

    export default class HelloWorldWebPart extends BaseClientSideWebPart<IHelloWorldWebPartProps> {
      // ...
    }
    ```

1. Whenever you need a valid request digest token, retrieve a reference to the DigestCache service, and call its **fetchDigest()** method:

    ```typescript
    // ...
    import { IDigestCache, DigestCache } from '@microsoft/sp-http';

    export default class HelloWorldWebPart extends BaseClientSideWebPart<IHelloWorldWebPartProps> {
      protected onInit(): Promise<void> {
        return new Promise<void>((resolve: () => void, reject: (error: any) => void): void => {
          const digestCache: IDigestCache = this.context.serviceScope.consume(DigestCache.serviceKey);
          digestCache.fetchDigest(this.context.pageContext.web.serverRelativeUrl).then((digest: string): void => {
            // use the digest here
            resolve();
          });
        });
      }

      // ...
    }
    ```
