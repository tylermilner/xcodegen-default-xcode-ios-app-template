# xcodegen-default-xcode-ios-app-template

A basic iOS app that uses [XcodeGen](https://github.com/yonaskolb/XcodeGen) for Xcode project file generation while attempting to mimic to the default Xcode iOS "App" template that you can use when creating a new Xcode project via File --> New --> Project.

## Getting Started

1. [Install XcodeGen](https://github.com/yonaskolb/XcodeGen/tree/master?tab=readme-ov-file#installing) using [Homebrew](https://brew.sh):

```shell
brew install xcodegen
```

2. Clone and open repo directory:

```shell
git clone https://github.com/tylermilner/xcodegen-default-xcode-ios-app-template.git && cd xcodegen-default-xcode-ios-app-template
```

3. Run XcodeGen:

```shell
xcodegen
```

4. Open the generated `xcodeproj` file:

```shell
open MyApp.xcodeproj
```

If you would like to customize the template generation process, make the necessary changes in `project.yml` and then run `xcodegen` again.

## Why?

Upon searching for ways to programmatically generate standard iOS Xcode projects, I found that [XcodeGen](https://github.com/yonaskolb/XcodeGen) and [Tuist](https://github.com/tuist/tuist) both seemed like good modern options. I opted for XcodeGen since it uses `yaml` for the configuration file, although the `swift`-based configuration of Tuist is also quite appealing.

After generating my first project using XcodeGen, I noticed that the generated project was not quite the same as what I got with an Xcode-generated project. For most people, it's probably no big deal since they are using XcodeGen on pre-existing or complex projects in order to avoid checking in the `xcodeproj` file to source control.

However, my primary use case for XcodeGen is to spin up fresh, bare-bones projects quickly. This project is an attempt to get an XcodeGen-generated project to match the default Xcode-generated project as closely as possible, giving me a clean foundation to start evolving my projects from.

## Determining the XcodeGen Project Config

The primary reference to determine the necessary contents of the `project.yml` was a default SwiftUI-based app called "MyApp" created using Xcode `15.2` and compared to the following bare-bones project created using XcodeGen `2.39.1`:

```yaml
name: MyApp
targets:
  MyApp:
    type: application
    platform: iOS
    sources:
      - MyApp
```

![Xcode "File" -> "New" --> "Project" app template selection.](./docs/images/xcode-file-new-project-app-template-1.png)

![Xcode new project setup options.](./docs/images/xcode-file-new-project-app-template-2.png)

## Discrepancies with Xcode-Generated Projects

Even after making the necessary changes to `project.yml`, there are some project/target settings that technically stray slightly from what you would encounter when creating a new project via the Xcode UI.

See [Discrepancies with Xcode-Generated Projects](./docs/discrepancies-with-xcode-generated-projects.md) for more details.

## License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.
