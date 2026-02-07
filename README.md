# SwiftfulPurchasingRevenueCat

Add [RevenueCat](https://www.revenuecat.com/docs) support to a Swift application through the [SwiftfulPurchasing](https://github.com/SwiftfulThinking/SwiftfulPurchasing) framework.

## Setup

<details>
<summary> Details (Click to expand) </summary>
<br>

Add SwiftfulPurchasingRevenueCat to your project.

```
https://github.com/SwiftfulThinking/SwiftfulPurchasingRevenueCat.git
```

Import the package.

```swift
import SwiftfulPurchasingRevenueCat
```

Configure `PurchaseManager` with `RevenueCatPurchaseService`:

```swift
#if DEBUG
let purchaseManager = PurchaseManager(service: MockPurchaseService(), logger: logManager)
#else
let purchaseManager = PurchaseManager(service: RevenueCatPurchaseService(apiKey: revenueCatApiKey), logger: logManager)
#endif
```

</details>

## Example Actions

You can call `logIn` every app launch.

```swift
let products = try await purchaseManager.getProducts(productIds: ["product.yearly"])
try await purchaseManager.purchaseProduct(productId: "product.yearly")
try await purchaseManager.restorePurchase()
try await purchaseManager.logIn(userId: "user_123", userAttributes: PurchaseProfileAttributes(email: "hello@example.com"))
try await purchaseManager.logOut()
try await purchaseManager.checkTrialEligibility(productId: "product.yearly")
try await purchaseManager.updateProfileAttributes(attributes: PurchaseProfileAttributes(mixpanelDistinctId: mixpanelId))
```

## RevenueCat Documentation

- [RevenueCat Getting Started](https://www.revenuecat.com/docs/getting-started)
- [RevenueCat iOS SDK](https://github.com/RevenueCat/purchases-ios)

## Claude Code

This package is used via [SwiftfulPurchasing](https://github.com/SwiftfulThinking/SwiftfulPurchasing). See the parent package's `.claude/swiftful-purchasing-rules.md` for usage guidelines and integration advice for projects using [Claude Code](https://claude.ai/claude-code).

## Platform Support

- **iOS 17.0+**
- **macOS 14.0+**

## License

SwiftfulPurchasingRevenueCat is available under the MIT license.
