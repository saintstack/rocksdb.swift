# rocksdb.swift

This library provides Swift bindings for [rocksdb](https://rocksdb.org).
Forked from [rocksdb.swift](https://github.com/koraykoska/rocksdb.swift),
stripped down, and then updated to use rocksdb v8.1.1 and swift 5.9.

Per the fork source, uses the rocksdb `c.h` interface rather than swift c++
interop. Playing with the latter, need to annotation the rocksdb source to
smooth the integration as well as do work to avoid default copying of c++
objects/types that swift does to make c++ objects 'safe' in swift context.
The clang modulemaps and rocksdb code layout don't play together too well
either so skipped on c++ interop for now. 

## Building

First do the below to generate `build_version.cc` needed by the build. It
will generate and then remove the `unify.cc` file and as a side-effect,
the `build_version.cc` is produced (Writing into the package directory
from the swift package build is disallowed; pre-build steps via the likes
of `swiftgen` are all about templates rather than running a simple make 
TODO).
```
 cd Sources/librocksdb/upstream
 make unity.cc && rm -f unity.cc
```

Now you can do your usual
```
swift build
```

## Compatibility

You can use this library with Swift Package Manager and Cocoapods on iOS, macOS, tvOS, watchOS and Linux.

## Installation

### CocoaPods

RocksDB is available through [CocoaPods](http://cocoapods.org/). To install it, simply add the following line to your Podfile:

```Ruby
pod 'rocksdb.swift'
```

### Swift Package Manager

RocksDB is compatible with Swift Package Manager (Swift 5 and above). Simply add it to the dependencies in your Package.swift.

```Swift
dependencies: [
    .package(url: "https://github.com/Ybrin/rocksdb.swift.git", from: "6.4.15")
]
```

And then add it to your target dependencies:

```Swift
targets: [
    .target(
        name: "MyProject",
        dependencies: ["RocksDB"]),
    .testTarget(
        name: "MyProjectTests",
        dependencies: ["MyProject"])
]
```

After the installation you can import RocksDB in your .swift files.

```Swift
import Web3
```

## Usage

For now, check out the tests for examples on how to use this wrapper. Contributions to add more examples are happily welcome.

## Versioning

Major and Minor Version numbers are kept in sync with the upstream rocksdb library. Patch version varies.

## License

rocksdb.swift is available under the MIT license. Copyright for rocksdb belongs to facebook.
