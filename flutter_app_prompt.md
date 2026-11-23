### نکات زیر دقیق و دقیق در نظر گرفته شود و پیاده سازی شود.
- اپلیکیشن موبایل با **Flutter** برای اندروید و iOS ساخته شود؛ تمام داده‌های کاربر فقط روی دستگاه کاربر در **دیتابیس محلی** ذخیره شوند و هیچ سرور اختصاصی، ثبت‌نام اجباری یا حساب کاربری وجود نداشته باشد.
- واژه «آفلاین» یا «بدون اینترنت» در هیچ‌جای اپلیکیشن استفاده نشود و به این مفهوم هیچ اشاره‌ای نشود.
- نام هیچ مارکتی در هیچ قسمت قابل مشاهده اپلیکیشن (UI، متن‌ها، خطاها، دیالوگ‌ها) نمایش داده نشود.
- قیمت عددی اشتراک‌ها در هیچ قسمت رابط کاربری نمایش داده نشود؛ پلن‌ها فقط با عناوین «ماهیانه، سه‌ماهه، شش‌ماهه، سالیانه، پرداخت یک‌باره» معرفی شوند.
- رابط کاربری کاملاً فارسی و راست‌چین (RTL) استاندارد، مدرن، بسیار زیبا و شکیل، واکنش‌گرا و سازگار با گوشی و تبلت باشد.
- تم تاریک و روشن دقیق و استاندارد در همه صفحات، دیالوگ‌ها، BottomSheet‌ها و ویجت‌ها داشته باشد؛ هیچ رنگ هاردکد (hardcoded) استفاده نشود؛ پیش‌فرض از سیستم پیروی کند (ThemeMode.system) و تغییر دستی از تنظیمات با ذخیره انتخاب کاربر امکان‌پذیر باشد.
-  همه دکمه‌های «قبلی / بازگشت» سمت راست صفحه باشند و آیکون فلش آن‌ها به سمت راست اشاره کند؛ دکمه بازگشت AppBar نیز فلش رو به راست داشته باشد.
- همه دکمه‌های «بعدی / ادامه / مرحله بعد» سمت چپ صفحه باشند و آیکون فلش آن‌ها به سمت چپ اشاره کند.
-  صفحه Splash جذاب و متحرک در هر بار اجرای برنامه نمایش داده شود.
-  صفحه خوشامدگویی و راه‌اندازی اولیه (Onboarding) الزامی باشد، فقط بار اول اجرا نمایش داده شود و تا تکمیل آن ورود به صفحه اصلی ممکن نباشد.
-  در Onboarding اطلاعات موردنیاز محصول از کاربر گرفته شود (مانند نام یا لقب کاربر و اطلاعات پایه مرتبط با موضوع اپ) و پذیرش «شرایط استفاده» با تیک تأیید در همان مسیر گرفته شود.
- امکان ویرایش همه اطلاعات اولیه از داخل تنظیمات فراهم باشد؛ صفحه تنظیمات کامل، منظم و حرفه‌ای باشد.
- صفحات تنظیمات شامل این موارد باشد: اطلاعات کاربر (ویرایش اطلاعات اولیه)، نمایش/تغییر تم (روشن، تاریک، سیستم)، اشتراک و مدیریت خرید (وضعیت پرمیوم، تمدید، بازیابی خریدها)، پشتیبان‌گیری و بازیابی، شرایط استفاده، پشتیبانی، معرفی به دوستان، ثبت بازخورد، دیگر محصولات، درباره اپلیکیشن (نمایش شماره نسخه)، حذف کامل داده‌ها (با دیالوگ تأیید) و هر مورد دیگری که بسته به ماهیت اپلیکیشن نیاز است.
- ساختار و مستندات رسمی سه مارکت کافه‌بازار، مایکت و سیب‌اپ دقیق بررسی شود و پرداخت درون‌برنامه‌ای هر مارکت مطابق SDK و قوانین رسمی همان مارکت پیاده‌سازی شود.
- اپلیکیشن برای سه مارکت پیاده‌سازی شود: کافه‌بازار (اندروید)، مایکت (اندروید)، سیب‌اپ (iOS).
- با Flutter Flavor سه خروجی مستقل، مجزا و قابل انتشار ساخته شود (سه نقطه ورود جدا، مثلاً main_cafebazaar.dart، main_myket.dart، main_sibapp.dart) که با هم هیچ تداخلی نداشته باشند.
- برای کافه‌بازار و مایکت دو AndroidManifest جداگانه وجود داشته باشد (src/cafebazaar/AndroidManifest.xml و src/myket/AndroidManifest.xml) و در بیلد هر فلاور، کتابخانه و پیکربندی مارکت دیگر به هیچ شکل استفاده یا لود نشود.
- مدیریت خرید، اعتبارسنجی تراکنش، تمدید و بازیابی خریدها به‌صورت کامل پیاده‌سازی شود.
- در نسخه دیباگ و در حالت flutter run، تمام قابلیت‌های پرمیوم بدون نیاز به خرید فعال باشند.
- تمام متن‌ها، خطاها و پیام‌های پرداخت مستقل از نام مارکت نوشته شوند، ولی علت دقیق هر خطا به کاربر نمایش داده شود تا قابل پیگیری توسط پشتیبانی باشد.
- تمام تنظیمات، مقادیر متغیر و تنظیمات محیطی از فایل‌های ENV (جدا برای هر فلاور) خوانده شوند و هیچ مقداری هاردکد نشود؛ شامل: شناسه محصولات (SKU)، لینک صفحه اپ و لینک صفحه توسعه‌دهنده در هر مارکت، ایمیل پشتیبانی، مقادیر مورد استفاده SDKها و هر مقدار متغیر دیگر.
- شناسه بسته (Application ID) و شناسه نسخه Debug جداگانه و مشخص تعریف شوند: برای هر فلاور applicationId مستقل + پسوند debug.
- قابلیت خروجی گرفتن از کل تنظیمات و دیتای کاربر به‌صورت Backup و Restore وجود داشته باشد (یک فایل خروجی قابل ذخیره/اشتراک‌گذاری و بازگردانی با تأیید کاربر) و در «شرایط استفاده» صراحتاً ذکر شود که مسئولیت نگهداری از داده‌ها و فایل پشتیبان به عهده خود کاربر است.
- گزینه «شرایط استفاده» وجود داشته باشد که در آن تمام مسئولیت و نگهداری از داده‌ها به عهده کاربر گذاشته شود و هیچ مسئولیتی بر عهده طراح نباشد.
- گزینه پشتیبانی به آیدی @AppSupportHQ متصل شود.
- خروج از اپ فقط با دو بار زدن دکمه برگشت انجام شود: بار اول Toast نمایش داده شود و بار دوم برنامه خارج شود؛ این رفتار فقط در صفحه اصلی فعال باشد.
- درخواست ثبت امتیاز و نظر با لینک مستقیم صفحه اپلیکیشن در مارکت مربوطه، در جاهای مهم و به‌صورت هوشمند (بعد از تجربه موفق و با محدودیت تکرار) به کاربر نمایش داده شود.
- این لینک‌ها در جای مناسب قرار گیرند: معرفی به دوستان (اشتراک‌گذاری همراه پیام تبلیغاتی)، ثبت بازخورد (لینک به صفحه اپ در مارکت جاری)، دیگر محصولات (لینک به لیست محصولات توسعه‌دهنده در مارکت جاری، مانند لیست محصولات کافه‌بازار).
- دسترسی‌ها و مجوزهای سیستم‌عامل فقط هنگام نیاز و در لحظه استفاده درخواست شوند.
- برای نسخه ریلیز iOS (سیب‌اپ) یک GitHub Action کامل قرار داده شود که خروجی release بدون امضا بگیرد  و در مسیر ".github/workflows/main.yml" قرار دهد نمونه این فایل را در پایین قرار دادم
- در فایل‌های کد هیچ کامنتی درج نشود.
- هیچ المنت یا ویجتی Overflow نشود؛ با SafeArea، Expanded، Flexible و SingleChildScrollView کنترل شود و دقیق بررسی شود.
- پیش از تحویل، همه کدها دقیق بررسی شوند؛ نیازی به اجرای تست نیست ولی کد نباید مشکل سینتکس یا منطق داشته باشد.
- هیچ SDK تبلیغاتی یا آنالیتیکس اضافه نشود.
- حالت‌های خالی، لودینگ و خطا در همه لیست‌ها و صفحات طراحی شوند و برای عملیات مخرب (حذف داده، بازگردانی پشتیبان) دیالوگ تأیید گرفته شود.
- نمونه فایل های موفق که در محیط من بدون مشکل اجرا می شود را در پایین لیست کردم مشابه همان ها ایجاد کن.
- هنگام پیاده‌سازی Flavorهای مارکت، دقت کن پلاگین‌ها و وابستگی‌های پرداخت مایکت و کافه‌بازار هم‌زمان در یک Flavor حضور نداشته باشند؛ وابستگی هر درگاه فقط در Flavor مخصوص خودش فعال باشد.
- محیط تست و اجرا و بیلد پروژه من به شرح زیر است سازگار با این محیط پیاده سازی کن
    - Windows 11 Enterprise
    - Flutter: 3.47.9
    - Dart: 3.13.7
    - DevTools: 2.60.0
    - Pub Mirror: https://pub.myket.ir
    - Android SDK: 36.1.0
    - Build-Tools: 36.1.0
    - ADB: 37.0.1
    - Java (JBR): 21.0.10
    - Gradle Wrapper: 8.14
    - Android Gradle Plugin: 8.11.1
    - Kotlin: 2.2.20
    - Java Source/Target: 17


---


###### کتابخانه‌های پرداخت درون‌برنامه‌ای در pubspec.yaml
```
flutter_poolakey: ^2.2.0+1.0.0
myket_iap: ^1.1.12
```

###### settings.gradle حتما از ریپو https://maven.myket.ir استفاده شود
```
pluginManagement {
  repositories {
    maven { url = uri("https://maven.myket.ir/") }
  }
}
dependencyResolutionManagement {
  repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
  repositories {
    maven { url = uri("https://maven.myket.ir/") }
  }
}
```

###### build.gradle
```
buildscript {
  repositories {
    maven { url 'https://maven.myket.ir/' }
  }
}
allprojects {
  repositories {
    maven { url 'https://maven.myket.ir/' }
  }
}
```

###### .github/workflows/main.yml
```

name: iOS IPA Release

on:
  workflow_dispatch:
    inputs:
      tag:
        description: "Base release tag (e.g. v2.0)"
        required: true
        default: "v1.0"
        type: string

      flavors:
        description: "Comma-separated flavors (e.g. production,staging or default)"
        required: true
        default: "default"
        type: string

      bundle_ids:
        description: "Comma-separated Bundle IDs (same order as flavors; optional)"
        required: false
        type: string

      display_names:
        description: "Comma-separated display names (same order as flavors; optional)"
        required: false
        type: string

      url_schemes:
        description: "Comma-separated URL schemes (same order as flavors; optional)"
        required: false
        type: string

      market:
        description: "Application market"
        required: true
        default: "default"
        type: string

      extra_defines:
        description: "Additional Dart defines (comma-separated KEY=VALUE)"
        required: false
        type: string

      app_name:
        description: "Release and artifact name"
        required: true
        default: "app"
        type: string

      flutter_version:
        description: "Flutter version"
        required: true
        default: "3.47.7"
        type: string

permissions:
  contents: write

jobs:
  prepare:
    name: Prepare Build Matrix
    runs-on: ubuntu-latest
    outputs:
      flavors: ${{ steps.matrix.outputs.flavors }}
    steps:
      - name: Generate matrix
        id: matrix
        env:
          FLAVORS: ${{ inputs.flavors }}
        run: |
          python3 -c 'import os,json; f=[x.strip() for x in os.environ["FLAVORS"].split(",") if x.strip()]; assert f, "At least one flavor is required"; print("matrix="+json.dumps({"flavor":f}))' >> "$GITHUB_OUTPUT"

  build-ios:
    name: Build iOS (${{ matrix.flavor }})
    needs: prepare
    runs-on: macos-latest
    strategy:
      fail-fast: false
      matrix: ${{ fromJson(needs.prepare.outputs.flavors) }}

    steps:
      - name: Checkout
        uses: actions/checkout@v6

      - name: Setup Flutter
        uses: subosito/flutter-action@v2
        with:
          channel: stable
          flutter-version: ${{ inputs.flutter_version }}
          cache: true

      - name: Install Flutter dependencies
        run: flutter pub get

      - name: Configure iOS
        env:
          FLAVOR: ${{ matrix.flavor }}
          FLAVORS: ${{ inputs.flavors }}
          BUNDLE_IDS: ${{ inputs.bundle_ids }}
          DISPLAY_NAMES: ${{ inputs.display_names }}
          URL_SCHEMES: ${{ inputs.url_schemes }}
        run: |
          python3 <<'PY'
          import os
          import re

          def get_value(key):
              values = [x.strip() for x in os.environ.get(key, "").split(",")]
              flavors = [x.strip() for x in os.environ["FLAVORS"].split(",")]
              flavor = os.environ["FLAVOR"]
              if not os.environ.get(key):
                  return ""
              if len(values) != len(flavors):
                  raise ValueError(f"{key} must contain one value per flavor")
              return values[flavors.index(flavor)]

          bundle_id = get_value("BUNDLE_IDS")
          display_name = get_value("DISPLAY_NAMES")
          url_scheme = get_value("URL_SCHEMES")

          pbxproj = "ios/Runner.xcodeproj/project.pbxproj"

          if bundle_id:
              with open(pbxproj, encoding="utf-8") as f:
                  content = f.read()
              content = re.sub(
                  r"PRODUCT_BUNDLE_IDENTIFIER = [^;]+;",
                  f"PRODUCT_BUNDLE_IDENTIFIER = {bundle_id};",
                  content
              )
              with open(pbxproj, "w", encoding="utf-8") as f:
                  f.write(content)

          plist = "ios/Runner/Info.plist"

          if display_name:
              os.system(f"/usr/libexec/PlistBuddy -c 'Set :CFBundleDisplayName {display_name}' {plist}")

          if url_scheme:
              os.system(f"/usr/libexec/PlistBuddy -c 'Set :CFBundleURLTypes:0:CFBundleURLSchemes:0 {url_scheme}' {plist}")

          print(f"Flavor: {os.environ['FLAVOR']}")
          print(f"Bundle ID: {bundle_id or 'Project default'}")
          PY

      - name: Generate app icon
        env:
          FLAVOR: ${{ matrix.flavor }}
        run: |
          CONFIG="flutter_launcher_icons_${FLAVOR}.yaml"
          if [ "$FLAVOR" != "default" ] && [ -f "$CONFIG" ]; then
            dart run flutter_launcher_icons -f "$CONFIG"
          elif [ -f "flutter_launcher_icons.yaml" ]; then
            dart run flutter_launcher_icons -f flutter_launcher_icons.yaml
          fi

      - name: Build iOS
        env:
          FLAVOR: ${{ matrix.flavor }}
          MARKET: ${{ inputs.market }}
          EXTRA_DEFINES: ${{ inputs.extra_defines }}
        run: |
          ARGS=()
          ARGS+=(--dart-define="APP_FLAVOR=$FLAVOR")
          ARGS+=(--dart-define="APP_MARKET=$MARKET")

          IFS=',' read -ra DEFINES <<< "$EXTRA_DEFINES"
          for DEFINE in "${DEFINES[@]}"; do
            DEFINE="$(echo "$DEFINE" | xargs)"
            if [ -n "$DEFINE" ]; then
              ARGS+=(--dart-define="$DEFINE")
            fi
          done

          if [ "$FLAVOR" = "default" ]; then
            flutter build ios --release --no-codesign "${ARGS[@]}"
          else
            flutter build ios --release --no-codesign --flavor "$FLAVOR" "${ARGS[@]}"
          fi

      - name: Package IPA
        working-directory: build/ios/iphoneos
        env:
          APP_NAME: ${{ inputs.app_name }}
          FLAVOR: ${{ matrix.flavor }}
        run: |
          mkdir -p Payload
          cp -R Runner.app Payload/
          ditto -c -k --sequesterRsrc --keepParent Payload "${APP_NAME}-${FLAVOR}.ipa"

      - name: Upload IPA artifact
        uses: actions/upload-artifact@v7
        with:
          name: ${{ inputs.app_name }}-${{ matrix.flavor }}-ipa
          path: build/ios/iphoneos/${{ inputs.app_name }}-${{ matrix.flavor }}.ipa
          if-no-files-found: error

  release-ios:
    name: Release iOS (${{ matrix.flavor }})
    needs: [prepare, build-ios]
    runs-on: ubuntu-latest
    strategy:
      fail-fast: false
      matrix: ${{ fromJson(needs.prepare.outputs.flavors) }}

    steps:
      - name: Download IPA artifact
        uses: actions/download-artifact@v8
        with:
          name: ${{ inputs.app_name }}-${{ matrix.flavor }}-ipa
          path: dist

      - name: Create GitHub Release
        uses: softprops/action-gh-release@v3
        with:
          token: ${{ github.token }}
          tag_name: ${{ matrix.flavor == 'default' && inputs.tag || format('{0}-{1}', matrix.flavor, inputs.tag) }}
          target_commitish: ${{ github.sha }}
          name: iOS ${{ matrix.flavor }} ${{ inputs.tag }}
          body: |
            Automated iOS IPA build.

            Application: ${{ inputs.app_name }}
            Flavor: ${{ matrix.flavor }}
            Market: ${{ inputs.market }}
            Commit: ${{ github.sha }}
          files: dist/*.ipa
          overwrite_files: true
          fail_on_unmatched_files: true
```



#### sample android/build.gradle
```

buildscript {
    repositories {
        maven { url "https://maven.myket.ir/" }
        maven { url "https://maven.aliyun.com/repository/gradle-plugin" }
        maven { url "https://maven.aliyun.com/repository/google" }
        maven { url "https://maven.aliyun.com/repository/public" }
        google()
        mavenCentral()
        gradlePluginPortal()
    }
}

allprojects {
    repositories {
        maven { url "https://maven.myket.ir/" }

        maven {
            url "https://pub.myket.ir/download.flutter.io"
            content {
                includeGroupByRegex "io\\.flutter.*"
            }
        }

        maven {
            url "https://storage.googleapis.com/download.flutter.io"
            content {
                includeGroupByRegex "io\\.flutter.*"
            }
        }

        maven { url "https://maven.aliyun.com/repository/google" }
        maven { url "https://maven.aliyun.com/repository/public" }

        google()
        mavenCentral()
        maven { url "https://jitpack.io" }
    }
}

subprojects {
    afterEvaluate { project ->
        if (project.hasProperty("android")) {
            project.android {
                if (compileSdk == null || compileSdk < 36) {
                    compileSdk = 36
                }

                compileOptions {
                    sourceCompatibility = JavaVersion.VERSION_17
                    targetCompatibility = JavaVersion.VERSION_17
                }
            }
        }

        project.tasks.withType(org.jetbrains.kotlin.gradle.tasks.KotlinCompile).configureEach {
            kotlinOptions {
                jvmTarget = "17"
            }
        }
    }
}

rootProject.buildDir = file("../build")

subprojects {
    project.buildDir = file("${rootProject.buildDir}/${project.name}")
}

subprojects {
    project.evaluationDependsOn(":app")
}

tasks.register("clean", Delete) {
    delete rootProject.buildDir
}

```

#### android/app/build.gradle
```

plugins {
    id "com.android.application"
    id "kotlin-android"
    id "dev.flutter.flutter-gradle-plugin"
}

android {
    namespace = "com.example.app"
    compileSdk = 36
    ndkVersion = flutter.ndkVersion

    compileOptions {
        sourceCompatibility = JavaVersion.VERSION_17
        targetCompatibility = JavaVersion.VERSION_17
    }

    kotlinOptions {
        jvmTarget = "17"
    }

    defaultConfig {
        applicationId = "com.example.app"
        minSdkVersion = flutter.minSdkVersion
        targetSdk = 35
        versionCode = flutter.versionCode
        versionName = flutter.versionName
    }

    buildTypes {
        debug {
            applicationIdSuffix = ".debug"
            debuggable = true
        }

        release {
            signingConfig = signingConfigs.debug
            minifyEnabled = false
            shrinkResources = false
        }
    }
}

configurations.all {
    exclude group: "com.android.billingclient"
}

flutter {
    source = "../.."
}

```
#### android/settings.gradle
```

pluginManagement {
    def flutterSdkPath = {
        def properties = new Properties()
        file("local.properties").withInputStream {
            properties.load(it)
        }

        def flutterSdkPath = properties.getProperty("flutter.sdk")
        assert flutterSdkPath != null, "flutter.sdk not set in local.properties"

        return flutterSdkPath
    }()

    includeBuild("$flutterSdkPath/packages/flutter_tools/gradle")

    repositories {
        maven { url "https://maven.myket.ir/" }
        maven { url "https://maven.aliyun.com/repository/gradle-plugin" }
        maven { url "https://maven.aliyun.com/repository/google" }
        maven { url "https://maven.aliyun.com/repository/public" }

        google()
        mavenCentral()
        gradlePluginPortal()
    }
}

plugins {
    id("dev.flutter.flutter-plugin-loader") version "1.0.0"
    id("com.android.application") version "8.11.1" apply false
    id("org.jetbrains.kotlin.android") version "2.2.20" apply false
}

dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.PREFER_PROJECT)

    repositories {
        maven { url "https://maven.myket.ir/" }

        maven {
            url "https://pub.myket.ir/download.flutter.io"
            content {
                includeGroupByRegex "io\\.flutter.*"
            }
        }

        maven {
            url "https://storage.googleapis.com/download.flutter.io"
            content {
                includeGroupByRegex "io\\.flutter.*"
            }
        }

        maven { url "https://maven.aliyun.com/repository/google" }
        maven { url "https://maven.aliyun.com/repository/public" }

        google()
        mavenCentral()
        maven { url "https://jitpack.io" }
    }
}

include(":app")
```

#### sample android/gradle/wrapper/gradle-wrapper.properties
```
distributionBase=GRADLE_USER_HOME
distributionPath=wrapper/dists
zipStoreBase=GRADLE_USER_HOME
zipStorePath=wrapper/dists
distributionUrl=https\://services.gradle.org/distributions/gradle-8.14-all.zip
```
