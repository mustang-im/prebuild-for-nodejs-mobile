# prebuild-for-nodejs-mobile

> CLI tool to compile native modules to work on [nodejs-mobile](https://github.com/nodejs-mobile/nodejs-mobile)

## Usage

`cd` into the folder that contains your native addon (folder containing the `package.json`) and then run `prebuild-for-nodejs-mobile`, specifying one of the supported targets:

```sh
$ npx prebuild-for-nodejs-mobile
ERROR: Must specify a target to prebuild-for-nodejs-mobile, one of these:
  * ios-arm64-simulator
  * ios-arm64
  * ios-x64
  * android-arm
  * android-arm64
  * android-x64
```

Such as `ios-arm64`:

```sh
$ npx prebuild-for-nodejs-mobile ios-arm64
```

Use `--verbose` to see the whole compilation logs:

```sh
$ npx prebuild-for-nodejs-mobile ios-arm64 --verbose
```

For Android, you can specify the Android SDK version with `--sdkXX`, otherwise by default it will be `24`, the lowest supported.

```sh
$ npx prebuild-for-nodejs-mobile android-arm64 --sdk28
```

Set the environment variables `IOS_LIBNODE` and `ANDROID_LIBNODE` for compiling to custom version for libnode. The values can
either be an absolute path to a local lib or a remote URL containing the lib.

An `include.gypi` file is created with contents `{'variables':{'android_ndk_path':''}}` to prevent an error `gyp: Undefined variable android_ndk_path in binding.gyp while trying to load binding.gyp` for Android builds.

## Features

- [x] Compiles native modules for iOS
- [x] Compiles native modules for Android
- [x] Can customize the Android SDK target API version
- [x] Compiles Rust (either [Neon](https://neon-bindings.com) or [node-bindgen](https://github.com/infinyon/node-bindgen)) Node.js native modules
- [ ] Can customize build flags

## Versioning

This project does *NOT* follow SemVer, instead it aims to reflect the upstream Node.js version is is based on.

`prebuild-for-nodejs-mobile` version `A.B.C` is based on Node.js Mobile version `A.B.*`, while the `C` is incremented whenever there are *any* changes to our codebase, be them fixes, features or otherwise, breaking changes or not. For this reason we recommend you call this CLI using `npx prebuild-for-nodejs-mobile@A.B.C` to ensure you are using the correct version for your Node.js Mobile version.

## License

MIT
