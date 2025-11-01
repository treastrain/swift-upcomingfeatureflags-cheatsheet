# `SwiftSetting` extension for upcoming features for swift-tools-version 5.8 to 5.10 (Swift 5.8 - 5.10)

```swift
import PackageDescription

extension SwiftSetting {
    static let conciseMagicFile: Self = .enableUpcomingFeature("ConciseMagicFile")                                      // SE-0274, Swift 5.8,  SwiftPM 5.8+
    static let forwardTrailingClosures: Self = .enableUpcomingFeature("ForwardTrailingClosures")                        // SE-0286, Swift 5.3,  SwiftPM 5.8+
    static let bareSlashRegexLiterals: Self = .enableUpcomingFeature("BareSlashRegexLiterals")                          // SE-0354, Swift 5.7,  SwiftPM 5.8+
    static let deprecateApplicationMain: Self = .enableUpcomingFeature("DeprecateApplicationMain")                      // SE-0383, Swift 5.10, SwiftPM 5.10+
    static let importObjcForwardDeclarations: Self = .enableUpcomingFeature("ImportObjcForwardDeclarations")            // SE-0384, Swift 5.9,  SwiftPM 5.9+
    static let disableOutwardActorInference: Self = .enableUpcomingFeature("DisableOutwardActorInference")              // SE-0401, Swift 5.9,  SwiftPM 5.9+
    static let isolatedDefaultValues: Self = .enableUpcomingFeature("IsolatedDefaultValues")                            // SE-0411, Swift 5.10, SwiftPM 5.10+
    static let globalConcurrency: Self = .enableUpcomingFeature("GlobalConcurrency")                                    // SE-0412, Swift 5.10, SwiftPM 5.10+
    static let existentialAny: Self = .enableUpcomingFeature("ExistentialAny")                                          // SE-0335, Swift 5.6,  SwiftPM 5.8+
}
```

## [`CaseIterable`](https://developer.apple.com/documentation/swift/caseiterable) Conformance

```swift
extension SwiftSetting: @retroactive CaseIterable {
    public static var allCases: [Self] {
        [
            .conciseMagicFile,
            .forwardTrailingClosures,
            .bareSlashRegexLiterals,
            .deprecateApplicationMain,
            .importObjcForwardDeclarations,
            .disableOutwardActorInference,
            .isolatedDefaultValues,
            .globalConcurrency,
            .existentialAny,
        ]
    }
}
```

# License

This cheatsheet by [@treastrain](https://github.com/treastrain) is marked with [CC0 1.0 Universal](http://creativecommons.org/publicdomain/zero/1.0?ref=chooser-v1). To view a copy of this license, visit http://creativecommons.org/publicdomain/zero/1.0?ref=chooser-v1
