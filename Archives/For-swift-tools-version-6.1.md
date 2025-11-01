# `SwiftSetting` extension for upcoming features for swift-tools-version 6.1 (Swift 6.1)

## For Swift Language Version 6

```swift
import PackageDescription

extension SwiftSetting {
    static let existentialAny: Self = .enableUpcomingFeature("ExistentialAny")                        // SE-0335, Swift 5.6,  SwiftPM 5.8+
    static let internalImportsByDefault: Self = .enableUpcomingFeature("InternalImportsByDefault")    // SE-0409, Swift 6.0,  SwiftPM 6.0+
    static let memberImportVisibility: Self = .enableUpcomingFeature("MemberImportVisibility")        // SE-0444, Swift 6.1,  SwiftPM 6.1+
}
```

### [`CaseIterable`](https://developer.apple.com/documentation/swift/caseiterable) Conformance

```swift
extension SwiftSetting: @retroactive CaseIterable {
    public static var allCases: [Self] {
        [
            .existentialAny,
            .internalImportsByDefault,
            .memberImportVisibility,
        ]
    }
}
```

<details>
<summary><h2>For Swift Language Version 5</h2></summary>

```swift
import PackageDescription

extension SwiftSetting {
    static let conciseMagicFile: Self = .enableUpcomingFeature("ConciseMagicFile")                                      // SE-0274, Swift 5.8,  SwiftPM 5.8+
    static let forwardTrailingClosures: Self = .enableUpcomingFeature("ForwardTrailingClosures")                        // SE-0286, Swift 5.3,  SwiftPM 5.8+
    static let strictConcurrency: Self = .enableUpcomingFeature("StrictConcurrency")                                    // SE-0337, Swift 6.0,  SwiftPM 6.0+
    static let bareSlashRegexLiterals: Self = .enableUpcomingFeature("BareSlashRegexLiterals")                          // SE-0354, Swift 5.7,  SwiftPM 5.8+
    static let deprecateApplicationMain: Self = .enableUpcomingFeature("DeprecateApplicationMain")                      // SE-0383, Swift 5.10, SwiftPM 5.10+
    static let importObjcForwardDeclarations: Self = .enableUpcomingFeature("ImportObjcForwardDeclarations")            // SE-0384, Swift 5.9,  SwiftPM 5.9+
    static let disableOutwardActorInference: Self = .enableUpcomingFeature("DisableOutwardActorInference")              // SE-0401, Swift 5.9,  SwiftPM 5.9+
    static let isolatedDefaultValues: Self = .enableUpcomingFeature("IsolatedDefaultValues")                            // SE-0411, Swift 5.10, SwiftPM 5.10+
    static let globalConcurrency: Self = .enableUpcomingFeature("GlobalConcurrency")                                    // SE-0412, Swift 5.10, SwiftPM 5.10+
    static let inferSendableFromCaptures: Self = .enableUpcomingFeature("InferSendableFromCaptures")                    // SE-0418, Swift 6.0,  SwiftPM 6.0+
    static let implicitOpenExistentials: Self = .enableUpcomingFeature("ImplicitOpenExistentials")                      // SE-0352, Swift 5.7,  SwiftPM 6.0+
    static let regionBasedIsolation: Self = .enableUpcomingFeature("RegionBasedIsolation")                              // SE-0414, Swift 6.0,  SwiftPM 6.0+
    static let dynamicActorIsolation: Self = .enableUpcomingFeature("DynamicActorIsolation")                            // SE-0423, Swift 6.0,  SwiftPM 6.0+
    static let nonfrozenEnumExhaustivity: Self = .enableUpcomingFeature("NonfrozenEnumExhaustivity")                    // SE-0192, Swift 6.0,  SwiftPM 6.0+
    static let globalActorIsolatedTypesUsability: Self = .enableUpcomingFeature("GlobalActorIsolatedTypesUsability")    // SE-0434, Swift 6.0,  SwiftPM 6.0+
    static let existentialAny: Self = .enableUpcomingFeature("ExistentialAny")                                          // SE-0335, Swift 5.6,  SwiftPM 5.8+
    static let internalImportsByDefault: Self = .enableUpcomingFeature("InternalImportsByDefault")                      // SE-0409, Swift 6.0,  SwiftPM 6.0+
    static let memberImportVisibility: Self = .enableUpcomingFeature("MemberImportVisibility")                          // SE-0444, Swift 6.1,  SwiftPM 6.1+
}
```

### [`CaseIterable`](https://developer.apple.com/documentation/swift/caseiterable) Conformance

```swift
extension SwiftSetting: @retroactive CaseIterable {
    public static var allCases: [Self] {
        [
            .conciseMagicFile,
            .forwardTrailingClosures,
            .strictConcurrency,
            .bareSlashRegexLiterals,
            .deprecateApplicationMain,
            .importObjcForwardDeclarations,
            .disableOutwardActorInference,
            .isolatedDefaultValues,
            .globalConcurrency,
            .inferSendableFromCaptures,
            .implicitOpenExistentials,
            .regionBasedIsolation,
            .dynamicActorIsolation,
            .nonfrozenEnumExhaustivity,
            .globalActorIsolatedTypesUsability,
            .existentialAny,
            .internalImportsByDefault,
            .memberImportVisibility,
        ]
    }
}
```

</details>

# License

This cheatsheet by [@treastrain](https://github.com/treastrain) is marked with [CC0 1.0 Universal](http://creativecommons.org/publicdomain/zero/1.0?ref=chooser-v1). To view a copy of this license, visit http://creativecommons.org/publicdomain/zero/1.0?ref=chooser-v1
