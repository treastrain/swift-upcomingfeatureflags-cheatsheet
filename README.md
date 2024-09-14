# Swift Upcoming Feature Flags Cheatsheet

This is a cheatsheet for applying [Swift's Upcoming Feature Flags](https://www.swift.org/blog/using-upcoming-feature-flags) to your `Package.swift` easily.

> [!NOTE]
> This cheatsheet only includes those that have been implemented in the release. It does not include accepted ones, etc. \
> This does not include Experimental Features.

## Usage

Copy and paste either "Short" or "Full" into your `Package.swift`.

```swift
import PackageDescription

// Paste here 📋

let package = Package(
    name: "Package Name",
    targets: [
        .target(
            name: "Target Name",
            swiftSettings: [
                .existentialAny // <-- Specify easily using completion 🥳
            ]
        )
    ]
)
```

Or, copy and paste the [`CaseIterable`](https://developer.apple.com/documentation/swift/caseiterable) Conformance as needed.

```swift
import PackageDescription

// Paste here 📋

let package = Package(
    name: "Package Name",
    targets: [
        .target(
            name: "Target Name"
        )
    ]
)

// Set all flags to targets 🎉
package.targets
    .filter { ![.system, .binary, .plugin].contains($0.type) }
    .forEach { $0.swiftSettings = SwiftSetting.allCases }
```

## Choose the swift-tools-version

> [!TIP]
> If you are using swift-tools-version 6.0 and have Swift language mode 5 for the entire package or per target, you may want to use a combination of both.

<details>
<summary><h2>For swift-tools-version 6.0 (Swift 6.0)</h2></summary>

### Short
```swift
import PackageDescription

extension SwiftSetting {
    static let existentialAny: Self = .enableUpcomingFeature("ExistentialAny")                      // SE-0335, Swift 5.6,  SwiftPM 5.8+
    static let internalImportsByDefault: Self = .enableUpcomingFeature("InternalImportsByDefault")  // SE-0409, Swift 6.0,  SwiftPM 6.0+
}
```

#### [`CaseIterable`](https://developer.apple.com/documentation/swift/caseiterable) Conformance

```swift
extension SwiftSetting: @retroactive CaseIterable {
    public static var allCases: [Self] {[.existentialAny, .internalImportsByDefault]}
}
```

### Full

```swift
import PackageDescription

extension SwiftSetting {
    /// Introduce existential `any`
    /// - Version: Swift 5.6
    /// - Since: SwiftPM 5.8
    /// - SeeAlso: [SE-0335: Introduce existential `any`](https://github.com/apple/swift-evolution/blob/main/proposals/0335-existential-any.md)
    static let existentialAny: Self = .enableUpcomingFeature("ExistentialAny")
    /// Access-level modifiers on import declarations
    /// - Version: Swift 6.0
    /// - Since: SwiftPM 6.0
    /// - SeeAlso: [SE-0409: Access-level modifiers on import declarations](https://github.com/swiftlang/swift-evolution/blob/main/proposals/0409-access-level-on-imports.md)
    static let internalImportsByDefault: Self = .enableUpcomingFeature("InternalImportsByDefault")
}
```

#### [`CaseIterable`](https://developer.apple.com/documentation/swift/caseiterable) Conformance

```swift
extension SwiftSetting: @retroactive CaseIterable {
    public static var allCases: [Self] {
        [
            .existentialAny,
            .internalImportsByDefault,
        ]
    }
}
```

</details>

<details>
<summary><h2>For swift-tools-version 5.8 to 5.10 (Swift 5.8 - 5.10)</h2></summary>

### Short
```swift
import PackageDescription

extension SwiftSetting {
    static let forwardTrailingClosures: Self = .enableUpcomingFeature("ForwardTrailingClosures")              // SE-0286, Swift 5.3,  SwiftPM 5.8+
    static let existentialAny: Self = .enableUpcomingFeature("ExistentialAny")                                // SE-0335, Swift 5.6,  SwiftPM 5.8+
    static let bareSlashRegexLiterals: Self = .enableUpcomingFeature("BareSlashRegexLiterals")                // SE-0354, Swift 5.7,  SwiftPM 5.8+
    static let conciseMagicFile: Self = .enableUpcomingFeature("ConciseMagicFile")                            // SE-0274, Swift 5.8,  SwiftPM 5.8+
    static let importObjcForwardDeclarations: Self = .enableUpcomingFeature("ImportObjcForwardDeclarations")  // SE-0384, Swift 5.9,  SwiftPM 5.9+
    static let disableOutwardActorInference: Self = .enableUpcomingFeature("DisableOutwardActorInference")    // SE-0401, Swift 5.9,  SwiftPM 5.9+
    static let deprecateApplicationMain: Self = .enableUpcomingFeature("DeprecateApplicationMain")            // SE-0383, Swift 5.10, SwiftPM 5.10+
    static let isolatedDefaultValues: Self = .enableUpcomingFeature("IsolatedDefaultValues")                  // SE-0411, Swift 5.10, SwiftPM 5.10+
    static let globalConcurrency: Self = .enableUpcomingFeature("GlobalConcurrency")                          // SE-0412, Swift 5.10, SwiftPM 5.10+
}
```

#### [`CaseIterable`](https://developer.apple.com/documentation/swift/caseiterable) Conformance

```swift
extension SwiftSetting: CaseIterable {
    public static var allCases: [Self] {[.forwardTrailingClosures, .existentialAny, .bareSlashRegexLiterals, .conciseMagicFile, .importObjcForwardDeclarations, .disableOutwardActorInference, .deprecateApplicationMain, .isolatedDefaultValues, .globalConcurrency]}
}
```

### Full

```swift
import PackageDescription

extension SwiftSetting {
    /// Forward-scan matching for trailing closures
    /// - Version: Swift 5.3
    /// - Since: SwiftPM 5.8
    /// - SeeAlso: [SE-0286: Forward-scan matching for trailing closures](https://github.com/apple/swift-evolution/blob/main/proposals/0286-forward-scan-trailing-closures.md)
    static let forwardTrailingClosures: Self = .enableUpcomingFeature("ForwardTrailingClosures")
    /// Introduce existential `any`
    /// - Version: Swift 5.6
    /// - Since: SwiftPM 5.8
    /// - SeeAlso: [SE-0335: Introduce existential `any`](https://github.com/apple/swift-evolution/blob/main/proposals/0335-existential-any.md)
    static let existentialAny: Self = .enableUpcomingFeature("ExistentialAny")
    /// Regex Literals
    /// - Version: Swift 5.7
    /// - Since: SwiftPM 5.8
    /// - SeeAlso: [SE-0354: Regex Literals](https://github.com/apple/swift-evolution/blob/main/proposals/0354-regex-literals.md)
    static let bareSlashRegexLiterals: Self = .enableUpcomingFeature("BareSlashRegexLiterals")
    /// Concise magic file names
    /// - Version: Swift 5.8
    /// - Since: SwiftPM 5.8
    /// - SeeAlso: [SE-0274: Concise magic file names](https://github.com/apple/swift-evolution/blob/main/proposals/0274-magic-file.md)
    static let conciseMagicFile: Self = .enableUpcomingFeature("ConciseMagicFile")
    /// Importing Forward Declared Objective-C Interfaces and Protocols
    /// - Version: Swift 5.9
    /// - Since: SwiftPM 5.9
    /// - SeeAlso: [SE-0384: Importing Forward Declared Objective-C Interfaces and Protocols](https://github.com/apple/swift-evolution/blob/main/proposals/0384-importing-forward-declared-objc-interfaces-and-protocols.md)
    static let importObjcForwardDeclarations: Self = .enableUpcomingFeature("ImportObjcForwardDeclarations")
    /// Remove Actor Isolation Inference caused by Property Wrappers
    /// - Version: Swift 5.9
    /// - Since: SwiftPM 5.9
    /// - SeeAlso: [SE-0401: Remove Actor Isolation Inference caused by Property Wrappers](https://github.com/apple/swift-evolution/blob/main/proposals/0401-remove-property-wrapper-isolation.md)
    static let disableOutwardActorInference: Self = .enableUpcomingFeature("DisableOutwardActorInference")
    /// Deprecate `@UIApplicationMain` and `@NSApplicationMain`
    /// - Version: Swift 5.10
    /// - Since: SwiftPM 5.10
    /// - SeeAlso: [SE-0383: Deprecate `@UIApplicationMain` and `@NSApplicationMain`](https://github.com/apple/swift-evolution/blob/main/proposals/0383-deprecate-uiapplicationmain-and-nsapplicationmain.md)
    static let deprecateApplicationMain: Self = .enableUpcomingFeature("DeprecateApplicationMain")
    /// Isolated default value expressions
    /// - Version: Swift 5.10
    /// - Since: SwiftPM 5.10
    /// - SeeAlso: [SE-0411: Isolated default value expressions](https://github.com/apple/swift-evolution/blob/main/proposals/0411-isolated-default-values.md)
    static let isolatedDefaultValues: Self = .enableUpcomingFeature("IsolatedDefaultValues")
    /// Strict concurrency for global variables
    /// - Version: Swift 5.10
    /// - Since: SwiftPM 5.10
    /// - SeeAlso: [SE-0412: Strict concurrency for global variables](https://github.com/apple/swift-evolution/blob/main/proposals/0412-strict-concurrency-for-global-variables.md)
    static let globalConcurrency: Self = .enableUpcomingFeature("GlobalConcurrency")
}
```

#### [`CaseIterable`](https://developer.apple.com/documentation/swift/caseiterable) Conformance

```swift
extension SwiftSetting: CaseIterable {
    public static var allCases: [Self] {
        [
            .forwardTrailingClosures,
            .existentialAny,
            .bareSlashRegexLiterals,
            .conciseMagicFile,
            .importObjcForwardDeclarations,
            .disableOutwardActorInference,
            .deprecateApplicationMain,
            .isolatedDefaultValues,
            .globalConcurrency,
        ]
    }
}
```

</details>

## License

This cheatsheet by [@treastrain](https://github.com/treastrain) is marked with [CC0 1.0 Universal](http://creativecommons.org/publicdomain/zero/1.0?ref=chooser-v1). To view a copy of this license, visit http://creativecommons.org/publicdomain/zero/1.0?ref=chooser-v1
