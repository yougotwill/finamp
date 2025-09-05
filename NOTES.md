# Building for macOS

- You need rust installed and cargo setup correctly.

  ```yml
  # ~/.cargo/config.toml
  [net]
  git-fetch-with-cli = true
  ```

- You need to install cocoapods using `gem install cocoapods` and not a version manager like asdf or mise because flutter gets confused between ruby versions on the system and your version manager.

- When you run the build command you will need to do an ad-hoc sign on `Finamp.app` otherwise the app will crash immediately on launch. This is because the library `libisar.dylib` has signing issues when built without proper certificates and we are self signing the application.

```sh
flutter build macos --release && codesign --force --deep --sign - build/macos/Build/Products/Release/Finamp.app
```
