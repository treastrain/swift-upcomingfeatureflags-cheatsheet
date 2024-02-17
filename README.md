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
    .filter { ![.system, .binary, .plugin, .macro].contains($0.type) }
    .forEach { $0.swiftSettings = SwiftSetting.allCases }
```

## Short
```swift
import PackageDescription

extension SwiftSetting {
    static let forwardTrailingClosures: Self = .enableUpcomingFeature("ForwardTrailingClosures")              // SE-0286, Swift 5.3,  SwiftPM 5.8+
    static let strictConcurrency: Self = .enableUpcomingFeature("StrictConcurrency")                          // SE-0337, Swift 5.6,  SwiftPM 5.8+
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

### [`CaseIterable`](https://developer.apple.com/documentation/swift/caseiterable) Conformance

```swift
extension SwiftSetting: CaseIterable {
    public static var allCases: [Self] {[.forwardTrailingClosures, .strictConcurrency, .existentialAny, .bareSlashRegexLiterals, .conciseMagicFile, .importObjcForwardDeclarations, .disableOutwardActorInference, .deprecateApplicationMain, .isolatedDefaultValues, .globalConcurrency]}
}
```

## Full

```swift
import PackageDescription

extension SwiftSetting {
    /// Forward-scan matching for trailing closures
    /// - Version: Swift 5.3
    /// - Since: SwiftPM 5.8
    /// - SeeAlso: [SE-0286: Forward-scan matching for trailing closures](https://github.com/apple/swift-evolution/blob/main/proposals/0286-forward-scan-trailing-closures.md)
    static let forwardTrailingClosures: Self = .enableUpcomingFeature("ForwardTrailingClosures")
    /// Incremental migration to concurrency checking
    /// - Version: Swift 5.6
    /// - Since: SwiftPM 5.8
    /// - SeeAlso: [SE-0337: Incremental migration to concurrency checking](https://github.com/apple/swift-evolution/blob/main/proposals/0337-support-incremental-migration-to-concurrency-checking.md)
    static let strictConcurrency: Self = .enableUpcomingFeature("StrictConcurrency")
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

### [`CaseIterable`](https://developer.apple.com/documentation/swift/caseiterable) Conformance

```swift
extension SwiftSetting: CaseIterable {
    public static var allCases: [Self] {
        [
            .forwardTrailingClosures,
            .strictConcurrency,
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

## License

This cheatsheet by [@treastrain](https://github.com/treastrain) is marked with [CC0 1.0 Universal](http://creativecommons.org/publicdomain/zero/1.0?ref=chooser-v1). To view a copy of this license, visit http://creativecommons.org/publicdomain/zero/1.0?ref=chooser-v1
