# Verification record

Documentation and checks: **1 November 2026**.

## Executed builds and JVM tests

Every application completed both `:app:assembleDebug` and `:app:testDebugUnitTest` successfully. The final JUnit XML reports **195 JVM tests**, zero failures, zero errors and zero skipped tests. These are JUnit test-method counts; loops over multiple input cases are not inflated into extra tests.

| Application | Debug build + JVM task | JVM tests | Scope of the existing tests |
|---|---|---:|---|
| [Rulivo](https://github.com/ILYAPROKOFEV101/Rulivo) | Passed | 146 | Geometry, command/state, tracking, localization and diagnostics; localization Gradle checks also passed. |
| [MapShots](https://github.com/ILYAPROKOFEV101/MapShots) | Passed | 18 | Mapping, collage models/export sizing, map bounds and gallery grouping, plus template case. |
| [PakNamazQiblaDua](https://github.com/ILYAPROKOFEV101/PakNamazQiblaDua) | Passed | 11 | Prayer/Qibla calculations, preferences and Tasbeeh state, plus template case. |
| [StatusSave](https://github.com/ILYAPROKOFEV101/StatusSave) | Passed | 1 | Generated arithmetic template only; no media/storage integration coverage implied. |
| [EMILoanCalculator](https://github.com/ILYAPROKOFEV101/EMILoanCalculator) | Passed | 1 | Generated arithmetic template only; no loan-algorithm coverage implied. |
| [GSTCalculatorIndia](https://github.com/ILYAPROKOFEV101/GSTCalculatorIndia) | Passed | 3 | Two focused GST methods (six cases each) and one template method. |
| [TrafficSignTestPakistanUrdu](https://github.com/ILYAPROKOFEV101/TrafficSignTestPakistanUrdu) | Passed | 15 | Fourteen domain/catalogue methods and one template method. |

The common invocation, from each application directory, was:

```sh
./gradlew :app:testDebugUnitTest :app:assembleDebug --console=plain --continue
```

Rulivo also passed `:app:checkLocalization` and `:app:testLocalizationCheck`. StatusSave's successful retry added `-PDUNTA_PARTNER_ID=0 -PDUNTA_APPLICATION_ID=0`, matching the safe defaults in its published Gradle properties example.

Gradle used the existing working checkouts and incremental caches. These were not clean-room builds from newly cloned repositories. They do not establish release-signing readiness, instrumented test success, real-device reliability or physical measurement accuracy. No Android device/emulator was connected; `connectedDebugAndroidTest`, lint and release builds were not run.

## Dependency download recovery

The first StatusSave attempt stopped before its test task because Maven Central returned HTTP 403 for `org.jetbrains.kotlin:kotlin-scripting-compiler-embeddable:2.0.21`. The first GST attempt stopped during dependency resolution because Java HTTPS could not complete a TLS handshake for `com.google.android.gms:play-services-ads-lite:23.5.0` from Google Maven.

Both artifacts were subsequently retrieved from the exact official repository endpoints. Their published SHA-1 checksums matched, and the files were restored to the user's local Gradle artifact cache before the successful retries. No application source, Gradle build script or repository endpoint was changed to resolve these download failures. Initial failed attempts are not represented as successful test runs.

## Documentation and material checks

- Found **35 Gradle project trees representing seven unique application IDs**: the current projects plus four transfer/verification copies per application. Archives and handover copies were left unchanged.
- Cross-checked product capabilities, dependency usage, dependency construction, persistence, asynchronous operations and Android APIs against the current source, rather than inferring features from dependency declarations.
- Checked relative Markdown links and HTML image sources against files actually included in Git. The published source repositories contain the referenced code, documentation, wrappers, tools and required local AAR files.
- Reviewed documentation images, provenance and metadata. QA screenshots, published store artwork, deterministic renderer output and launcher icons are explicitly distinguished. Original local assets were retained.
- Matched five Google Play listings by exact `applicationId`: Rulivo, GeoStamp, Pak Namaz, StatusSave and EMI Calculator. GST and Traffic Signs have no verified listing here. Run Tracker's supplied listing has no source in this workspace.
- Reviewed the new documentation and publish file lists for secrets and private data. Excluded local SDK configuration, signing material, build outputs, release bundles and IDE metadata. StatusSave and Traffic Signs publish a safe `gradle.properties.example` instead of their configured local properties file.
- Kept existing Rulivo policy documents containing personal contact information out of the initial publication. Removed personal home paths and provider-specific identifiers from the selected engineering notes. Provider/application routing identifiers in existing app code are not authentication keys; no authentication key or private signing material was added.
- Existing application source was published without editing its behavior. MapShots includes the source changes already present in the working checkout; its prior Git history was preserved. Documentation, selected images and repository exclusion/configuration examples were the edited materials.

## Published source snapshots

All application repositories use `main`. These commits identify the source snapshots reviewed by the documentation pass:

- [Rulivo · `2f4ca7f`](https://github.com/ILYAPROKOFEV101/Rulivo/commit/2f4ca7fca8ddb0f52747d2d283d3afad8fd576d7)
- [MapShots · `2a46bd6`](https://github.com/ILYAPROKOFEV101/MapShots/commit/2a46bd6a7244cc0b9bfc830992dbcdeb5b36d518)
- [PakNamazQiblaDua · `182066f`](https://github.com/ILYAPROKOFEV101/PakNamazQiblaDua/commit/182066f4db399873a1bf3f225f2ce083ef2703cb)
- [StatusSave · `5d3d79d`](https://github.com/ILYAPROKOFEV101/StatusSave/commit/5d3d79d20f13f1b5df303c761a71c8e64b5bda4b)
- [EMILoanCalculator · `bb0fd5d`](https://github.com/ILYAPROKOFEV101/EMILoanCalculator/commit/bb0fd5dc4786a58d1acca41919acd99794208ca5)
- [GSTCalculatorIndia · `016ca66`](https://github.com/ILYAPROKOFEV101/GSTCalculatorIndia/commit/016ca66502710cdd9602c762ecb9193919284ffa)
- [TrafficSignTestPakistanUrdu · `b383c9d`](https://github.com/ILYAPROKOFEV101/TrafficSignTestPakistanUrdu/commit/b383c9d50c954c86949b4e8d6176a8b1d2a9d31c)

Device-dependent limitations and incomplete implementations remain documented in the individual READMEs; passing JVM checks does not replace those integration checks.
