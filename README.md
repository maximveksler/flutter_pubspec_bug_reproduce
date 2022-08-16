# Bug

To reproduce run:

```
flutter pub remove equatable json_annotation meta uuid
flutter pub add equatable json_annotation meta uuid
```

## Initial state

```bash
m@m-inspiron5567:/tmp/flutter_pubspec_bug_reproduce$ cat pubspec.yaml
name: todos_api
description: The interface and models for an API providing access to todos.
version: 1.0.0+1
publish_to: none

environment:
  sdk: ">=2.17.0 <3.0.0"

dependencies:
  equatable: ^2.0.3
  json_annotation: ^4.4.0
  meta: ^1.3.0
  uuid: ^3.0.4

dev_dependencies:
  build_runner: ^2.0.0
  json_serializable: ^6.0.0
  test: ^1.17.0
  very_good_analysis: ^3.0.1
```

## Reproduction

```bash
m@m-inspiron5567:/tmp/flutter_pubspec_bug_reproduce$ flutter pub remove equatable json_annotation meta uuid
Resolving dependencies...

These packages are no longer being depended on:
- equatable 2.0.3
- uuid 3.0.6
Changed 2 dependencies!
m@m-inspiron5567:/tmp/flutter_pubspec_bug_reproduce$ flutter pub add equatable json_annotation meta uuid

Resolving dependencies...
+ equatable 2.0.3
+ uuid 3.0.6
```

## Result

```bash
m@m-inspiron5567:/tmp/flutter_pubspec_bug_reproduce$ cat pubspec.yaml
name: todos_api
description: The interface and models for an API providing access to todos.
version: 1.0.0+1
publish_to: none

environment:
  sdk: ">=2.17.0 <3.0.0"


dev_dependencies:
  build_runner: ^2.0.0
  json_serializable: ^6.0.0
  test: ^1.17.0
  very_good_analysis: ^3.0.1
dependencies: {equatable: ^2.0.3, json_annotation: ^4.6.0, meta: ^1.8.0, uuid: ^3.0.6}
```

# Flutter Doctor

```
m@m-inspiron5567:/tmp/flutter_pubspec_bug_reproduce$ flutter doctor -v
[✓] Flutter (Channel stable, 3.0.5, on Ubuntu 21.04 5.11.0-49-generic, locale en_IL)
    • Flutter version 3.0.5 at /home/m/snap/flutter/common/flutter
    • Upstream repository https://github.com/flutter/flutter.git
    • Framework revision f1875d570e (5 weeks ago), 2022-07-13 11:24:16 -0700
    • Engine revision e85ea0e79c
    • Dart version 2.17.6
    • DevTools version 2.12.2

[✓] Android toolchain - develop for Android devices (Android SDK version 32.1.0-rc1)
    • Android SDK at /home/m/Android/Sdk
    • Platform android-32, build-tools 32.1.0-rc1
    • ANDROID_SDK_ROOT = /home/m/Android/Sdk
    • Java binary at: /opt/android-studio/jre/bin/java
    • Java version OpenJDK Runtime Environment (build 11.0.12+0-b1504.28-7817840)
    • All Android licenses accepted.

[✓] Chrome - develop for the web
    • Chrome at google-chrome

[✓] Linux toolchain - develop for Linux desktop
    • clang version 6.0.0-1ubuntu2 (tags/RELEASE_600/final)
    • cmake version 3.10.2
    • ninja version 1.8.2
    • pkg-config version 0.29.1

[✓] Android Studio (version 2021.2)
    • Android Studio at /opt/android-studio
    • Flutter plugin can be installed from:
      🔨 https://plugins.jetbrains.com/plugin/9212-flutter
    • Dart plugin can be installed from:
      🔨 https://plugins.jetbrains.com/plugin/6351-dart
    • Java version OpenJDK Runtime Environment (build 11.0.12+0-b1504.28-7817840)

[✓] Android Studio (version 2021.1)
    • Android Studio at /usr/local/android-studio
    • Flutter plugin can be installed from:
      🔨 https://plugins.jetbrains.com/plugin/9212-flutter
    • Dart plugin can be installed from:
      🔨 https://plugins.jetbrains.com/plugin/6351-dart
    • Java version OpenJDK Runtime Environment (build 11.0.11+0-b60-7590822)

[✓] VS Code (version 1.70.1)
    • VS Code at /usr/share/code
    • Flutter extension version 3.46.0

[✓] Connected device (2 available)
    • Linux (desktop) • linux  • linux-x64      • Ubuntu 21.04 5.11.0-49-generic
    • Chrome (web)    • chrome • web-javascript • Google Chrome 104.0.5112.79

[✓] HTTP Host Availability
    • All required HTTP hosts are available

• No issues found!
```
