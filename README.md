# MMTAdmobSample
Example of how to use [MMTAdmobSample](https://github.com/marcojak/MauiMTAdmob) with [NET8](https://puresourcecode.com/tag/net8/). My focus is on the iOS version and in particular on rewarded advertisement. The first reward is displayed but the following is not.

## Fix for iOS

When I run the project, I get this error

> /usr/local/share/dotnet/packs/Microsoft.iOS.Sdk/17.0.8478/targets/Xamarin.Shared.Sdk.targets(3,3): Error: clang++ exited with code 1:
> Undefined symbols for architecture arm64:
> "OBJC_CLASS$_UMPConsentForm", referenced from:
> objc-class-ref in registrar.o
> "OBJC_CLASS$_UMPConsentInformation", referenced from:
> objc-class-ref in registrar.o
> "OBJC_CLASS$_UMPDebugSettings", referenced from:
> objc-class-ref in registrar.o
> "OBJC_CLASS$_UMPRequestParameters", referenced from:
> objc-class-ref in registrar.o
> ld: symbol(s) not found for architecture arm64
> clang: error: linker command failed with exit code 1 (use -v to see invocation)

To fix the error, only for iOS, I have to add those packages:

- Xamarin.Google.iOS.MobileAds
- Xamarin.Google.iOS.UserMessagingPlatform

For that, you can add the packages from Visual Studio or edit the project and add those lines:

```xml
<PackageReference Include="Xamarin.Google.iOS.MobileAds" Version="8.13.0.3"
    Condition="'$(TargetFramework)' == 'net8.0-ios'" />
<PackageReference Include="Xamarin.Google.iOS.UserMessagingPlatform" Version="1.2.0.5"
    Condition="'$(TargetFramework)' == 'net8.0-ios'" />
```

## Steps

### First example

- Open the example app
- Tap on **Load** the reward
- Tap on **Show** the reward
- Waiting and closing the reward
- Tap on **Load** the reward again
- Tap on **Show** the reward -> not displaying

### Second example

- Open the example app
- Tap on **Load** the reward
- Tap on **Show** the reward
- Waiting and closing the reward
- Tap on **Show** the reward -> not displaying

## Video

As you can see in the video, the first reward is displayed but after that no one is displayed. Only if I close the app and open it again, the reward is displayed again.

https://github.com/erossini/MMTAdmobSample/assets/9497415/449671fa-da4b-4654-9208-ddeac949c97d
