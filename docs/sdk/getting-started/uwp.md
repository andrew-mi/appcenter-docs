---
title: Get Started with UWP/WinUI
description: Get Started with UWP/WinUI
keywords: sdk
author: lucen-ms
ms.author: lucen
ms.date: 07/29/2021
ms.topic: article
ms.assetid: e66eeedb-5395-46ce-9526-9e22319a94d4
ms.tgt_pltfrm: uwp
---

# Get Started with UWP/WinUI
> [!div  class="op_single_selector"]
> * [Android](android.md)
> * [iOS](ios.md)
> * [iOS Extensions](ios-extensions.md)
> * [React Native](react-native.md)
> * [Xamarin](xamarin.md)
> * [UWP](uwp.md)
> * [WPF/WinForms](wpf-winforms.md)
> * [Unity](unity.md)
> * [macOS](macos.md)
> * [macOS Extensions](macos-extensions.md)
> * [tvOS](tvos.md)
> * [Cordova](cordova.md)

The App Center SDK uses a modular architecture so you can use any or all of the services.

Let's get started with setting up App Center SDK in your app to use App Center Analytics and App Center Crashes.

## 1. Prerequisites

Before you begin, make sure that the following prerequisites are met:

For UWP project:
* Your project is set up in Visual Studio 2017 Update 15.9 or later.
* You're targeting devices running Windows 10 build 16299 or later.
* Your project references Universal Windows Platform [6.2.8](https://www.nuget.org/packages/Microsoft.NETCore.UniversalWindowsPlatform/6.2.8) or later (this package is typically referenced implicitly).
* NuGet 4.3 or later.

For WinUI project:
* Your project is set up in Visual Studio 2019 Update 16.9 or later.
* You're targeting devices running Windows 10 build 17763 or later.
* Your project references WinUI 3 [0.8.0](https://docs.microsoft.com/windows/apps/windows-app-sdk/stable-channel#version-080) or later.

> [!NOTE]
> If you want to use Xamarin.Forms for UWP, follow the Xamarin [Getting started](~/sdk/getting-started/xamarin.md) documentation instead of this one.

## 2. Create your app in the App Center Portal to obtain the App Secret

If you have already created your app in the App Center portal, you can skip this step.

1. Sign up or log in and hit the blue button on the top right corner of the portal that says **Add new** and select **Add new app** from the dropdown menu.
2. Enter a name and an optional description for your app.
3. Select the appropriate OS and platform depending on your project as described above.
4. Hit the button at the bottom right that says **Add new app**.

Once you have created an app, you can obtain its **App Secret** on the **Settings** page on the App Center Portal. At the top right hand corner of the **Settings** page, click on the **triple vertical dots** and select `Copy app secret` to get your App Secret.

## 3. Add the App Center SDK modules

The App Center SDK can be integrated using Visual Studio, or the Package Manager Console.

### Visual Studio

* Open Visual Studio.
* Click **File** > **Open** and choose your solution.
* In the solution navigator, right-click **References** and choose **Manage NuGet Packages**.
* In the **Browse tab**, Search for **App Center**, and install **Microsoft.AppCenter.Analytics** and **Microsoft.AppCenter.Crashes** packages.

### Package Manager Console

* Open the console in [Visual Studio](https://visualstudio.microsoft.com/vs/). To do this, choose **Tools** > **NuGet Package Manager** > **Package Manager Console**.
* Type the following commands:

```shell
Install-Package Microsoft.AppCenter.Analytics
Install-Package Microsoft.AppCenter.Crashes
```

Now that you've integrated the SDK in your application, it's time to start the SDK and make use of the App Center services.

> [!NOTE]
> If you use the App Center SDK in a portable project (such as **Xamarin.Forms**), you must install the packages in each of the projects: the portable, Android, and iOS ones. To do that, you should open each sub-project and follow the corresponding steps described in [Visual Studio](#visual-studio) section.

## 4. Add the `Internet (Client)` capability

In Visual Studio solution explorer, double-click the **Package.appxmanifest** file for your application. Click the **Capabilities** tab then check the **Internet (Client)** capability.

## 5. Start the SDK

To use App Center, you must opt in to the module(s) that you want to use. By default no modules are started and you must explicitly call each of them when starting the SDK.

### 5.1 Add the using directives

Add the appropriate namespaces before you use our APIs.

```csharp
using Microsoft.AppCenter;
using Microsoft.AppCenter.Analytics;
using Microsoft.AppCenter.Crashes;
```

### 5.2 Add the `Start()` method

Add the following call to your application's **constructor**:

```csharp
AppCenter.Start("{Your App Secret}", typeof(Analytics), typeof(Crashes));
```

[!INCLUDE [app secret warning](../includes/app-secret-warning.md)]

[!INCLUDE [windows-configure-appcenter](includes/windows-configure-appcenter.md)]

### 5.3 Replace the placeholder with your App Secret

Make sure to replace `{Your App Secret}` text with the actual value for your application. The App Secret can be found on the **Getting Started** page or **Settings** page on the App Center portal.

The Getting Started page contains the above code sample with your App Secret in it, you can copy-paste the whole sample.

The example above shows how to use the `Start()` method and includes App Center Analytics.

Unless you explicitly specify each service as parameters in the start method, you can't use that App Center service. In addition, the `Start()` API can be used only once in the lifecycle of your app – all other calls will log a warning to the console and only the services included in the first call will be available.

Great, you're all set to visualize Analytics on the portal that the SDK collects automatically.

Look at the documentation for [App Center Analytics](~/sdk/analytics/windows.md) and [App Center Crashes](~/sdk/crashes/wpf-winforms.md) to learn how to customize and use more advanced functionalities of both services.
