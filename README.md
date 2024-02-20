# xcodegen-default-xcode-ios-app-template

A basic iOS app that uses [XcodeGen](https://github.com/yonaskolb/XcodeGen) for Xcode project file generation while attempting to mimic to the default Xcode iOS "App" template that you can use when creating a new Xcode project via File --> New --> Project.

![Xcode "File" -> "New" --> "Project" app template selection.](./docs/images/xcode-file-new-project-app-template-1.png)

![Xcode new project setup options.](./docs/images/xcode-file-new-project-app-template-2.png)

The primary reference to determine the necessary contents of the `project.yml` was a default SwiftUI-based app called "MyApp" created using Xcode `15.2` and compared to the following bare-bones project created using XcodeGen `2.38.0`:

```yaml
name: MyApp
targets:
  MyApp:
    type: application
    platform: iOS
    sources:
      - MyApp
```

## Getting Started

1. [Install XcodeGen](https://github.com/yonaskolb/XcodeGen/tree/master?tab=readme-ov-file#installing) - `brew install xcodegen`
2. Clone and open repo directory - `git clone https://github.com/tylermilner/xcodegen-default-xcode-ios-app-template.git && cd xcodegen-default-xcode-ios-app-template`
3. Run XcodeGen - `xcodegen`
4. Open the generated `xcodeproj` file - `open MyApp.xcodeproj`.

If you would like to customize the template generation process, make the necessary changes in `project.yml` and then run `xcodegen` again.

## Discrepancies with Xcode

When generating this project using XcodeGen, the following settings technically stray slightly from what you would encounter when creating a new project via the Xcode UI.

However, many of these changes are extremely minor or even just cosmetic differences in the Xcode UI so they _shouldn't_ have any adverse affects in real-world scenarios.

### Project-Level Discrepancies

#### Build Settings

##### Packaging

**Product Name (`PRODUCT_NAME`)**

* Xcode default - _nonexistent_ (unset/inherited value)
* XcodeGen default - _nonexistent_ (explicit/overridden value)

![Screenshot of comparison of "Packaging" section of Xcode project settings between default Xcode-generated project and XcodeGen-generated project.](./docs/images/xcode-xcodegen-project-settings-comparison-product-name.png)

This difference should have no real-world impact.

##### Swift Compiler - Code Generation

**Optimization Level - Release (`SWIFT_OPTIMIZATION_LEVEL`)**

* Xcode default - `Optimize for Speed [-O]` (unset/inherited value)
* XcodeGen default - `Optimize for Speed [-O]` (explicit/overridden value)

![Screenshot of comparison of "Swift Compiler - Code Generation" section of Xcode project settings between default Xcode-generated project and XcodeGen-generated project.](./docs/images/xcode-xcodegen-project-settings-comparison-optimization-level-release.png)

Since the overridden value is the same as the default value, this should not have any meaningful effect on the overall project settings.

##### Swift Compiler - Language

**Swift Language Version (`SWIFT_VERSION`)**

* Xcode default - `Unspecified` (unset/inherited value)
* XcodeGen default - `Swift 5` (explicit/overridden value)

![Screenshot of a comparison of "Swift Compiler - Language" section of Xcode project settings between default Xcode-generated project and XcodeGen-generated project.](./docs/images/xcode-xcodegen-project-settings-comparison-swift-language-version.png)

Although these values differ, there should be no real-world impact, assuming you want to use Swift 5 by default.

##### User-Defined

**`CLANG_CXX_LIBRARY`**

* Xcode default - _nonexistent_
* XcodeGen default - `libc++` (explicit/overridden value)

![Screenshot of a comparison of "User-Defined" section of Xcode project settings between default Xcode-generated project and XcodeGen-generated project.](./docs/images/xcode-xcodegen-project-settings-comparison-user-defined-clang-cxx-library.png)

This difference has the _potential_ to impact something if it makes use of the `CLANG_CXX_LIBRARY` variable during the build process, but I'm not currently aware of any adverse effects.

### Target-Level Discrepancies

#### MyApp - General

##### Frameworks, Libraries, and Embedded Content

* Xcode default - section title shows as "Frameworks, Libraries, and Embedded Content"
* XcodeGen default - section title shows as "Embedded Content"

![Screenshot of comparison of "Frameworks, Libraries, and Embedded Content" section of Xcode target general settings between Xcode-generated project and XcodeGen-generated project.](./docs/images/xcode-xcodegen-target-settings-comparison-embedded-content.png)

This difference appears to be purely cosmetic and should have no real-world impact.

#### MyApp - Build Settings

##### Architectures

**Base SDK (`SDKROOT`)**

* Xcode default - `iOS` (unset/inherited value)
* XcodeGen default - `iOS` (explicit/overridden value)

![Screenshot of comparison of "Architectures" section of Xcode target build settings between default Xcode-generated project and XcodeGen-generated project.](./docs/images/xcode-xcodegen-target-settings-comparison-base-sdk.png)

This difference should have no real-world impact.

##### Packaging

**Product Name (`PRODUCT_NAME`)**

* Xcode default - `MyApp` (explicit/overridden value)
* XcodeGen default - `MyApp` (unset/inherited value)

![Screenshot of comparison of "Packaging" section of Xcode target build settings between default Xcode-generated project and XcodeGen-generated project.](./docs/images/xcode-xcodegen-target-settings-comparison-product-name.png)

This difference should have no real-world impact.

##### Signing

**Code Signing Identity (`CODE_SIGN_IDENTITY`)**

* Xcode default - `Apple Development` (inherited from project)
* XcodeGen default - `Apple Development` (explicit/overridden value)

![Screenshot of comparison of "Signing" section of Xcode target build settings between default Xcode-generated project and XcodeGen-generated project.](./docs/images/xcode-xcodegen-target-settings-comparison-code-signing-identity.png)

This difference should have no real-world impact.

**Code Signing Style (`CODE_SIGN_STYLE`)**

* Xcode default - `Automatic` (explicit/overridden value)
* XcodeGen default - `Automatic` (unset/inherited value)

![Screenshot of comparison of "Signing" section of Xcode target build settings between default Xcode-generated project and XcodeGen-generated project.](./docs/images/xcode-xcodegen-target-settings-comparison-code-signing-style.png)

This difference should have no real-world impact.

##### Swift Compiler - Language

**Swift Language Version (`SWIFT_VERSION`)**

* Xcode default - `Swift 5` (explicit/overridden value)
* XcodeGen default - `Swift 5` (unset/inherited value)

![Screenshot of comparison of "Swift Compiler - Language" section of Xcode target build settings between default Xcode-generated project and XcodeGen-generated project.](./docs/images/xcode-xcodegen-target-settings-comparison-swift-language-version.png)

##### User-Defined

**`CLANG_CXX_LIBRARY`**

* Xcode default - _nonexistent_
* XcodeGen default - `libc++` (unset/inherited value)

![Screenshot of a comparison of "User-Defined" section of Xcode project settings between default Xcode-generated project and XcodeGen-generated project.](./docs/images/xcode-xcodegen-target-settings-comparison-user-defined-clang-cxx-library.png)

This difference has the _potential_ to impact something if it makes use of the `CLANG_CXX_LIBRARY` variable during the build process, but I'm not currently aware of any adverse effects.

#### MyApp - Build Phases

##### "Link Binary With Libraries" Build Step

* Xcode default - "Link Binary With Libraries" step exists
* XcodeGen default - "Link Binary With Libraries" step does not exist

![Screenshot of comparison of "Link Binary With Libraries" build phase of Xcode target settings between default Xcode-generated project and XcodeGen-generated project.](./docs/images/xcode-xcodegen-target-settings-comparison-build-phases.png)

This difference should have no real-world impact, at least until external libraries need to be integrated into the project, at which time, the "Link Binary With Libraries" build step can be added manually.

### Project Navigator Discrepancies

#### File Order

* Xcode default - `MyAppApp.swift` at top
    * `MyAppApp.swift`
    * `ContentView.swift`
    * `Assets.xcassets`
* XcodeGen default - alphabetical
    * `Assets.xcassets`
    * `ContentView.swift`
    * `MyAppApp.swift`

![Screenshot of comparison of file order between default Xcode-generated project and XcodeGen-generated project.](./docs/images/xcode-xcodegen-project-structure-comparison-file-order.png)

This difference should have no real-world impact and is easily correctable by dragging the files around to the desired order.

#### Products Folder

* Xcode default - _nonexistent_
* XcodeGen default - `Products/MyApp.app`

![Screenshot of comparison of products folder between default Xcode-generated project and XcodeGen-generated project.](./docs/images/xcode-xcodegen-project-structure-comparison-products-folder.png)

[As of Xcode 13](https://developer.apple.com/documentation/xcode-release-notes/xcode-13-release-notes#New-Features), Xcode no longer shows the "Products" folder in the project navigator, but it still exists in the file system. XcodeGen appears to be generating the "Products" folder explicitly. However, this difference should have no real-world impact.

## License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.
