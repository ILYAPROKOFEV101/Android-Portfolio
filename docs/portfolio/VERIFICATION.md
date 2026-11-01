# Verification record

Documentation and checks: **1 November 2026**. This record covers the three applications selected for the public portfolio: GeoStamp Camera / MapShots, Rulivo and StatusSave.

## Executed builds and JVM tests

All three applications completed `:app:assembleDebug` and `:app:testDebugUnitTest` successfully. The JUnit XML reports **165 JVM tests**, zero failures, zero errors and zero skips. Counts refer to JUnit test methods, including generated template cases.

| Application | Debug build + JVM task | JVM tests | Existing test scope |
|---|---|---:|---|
| [MapShots](https://github.com/ILYAPROKOFEV101/MapShots) | Passed | 18 | Photo/model mapping, collage models/export sizing, map bounds and gallery grouping, including a template check. |
| [Rulivo](https://github.com/ILYAPROKOFEV101/Rulivo) | Passed | 146 | Geometry, AR command/state, tracking, localization and diagnostics. |
| [StatusSave](https://github.com/ILYAPROKOFEV101/StatusSave) | Passed | 1 | Generated arithmetic template only; no storage or concurrency integration coverage implied. |

The common invocation, from each application directory, was:

```sh
./gradlew :app:testDebugUnitTest :app:assembleDebug --console=plain --continue
```

Rulivo also passed `:app:checkLocalization` and `:app:testLocalizationCheck`. StatusSave's successful retry added `-PDUNTA_PARTNER_ID=0 -PDUNTA_APPLICATION_ID=0`, matching its published safe Gradle properties example.

Gradle used the existing working checkouts and incremental caches. These were not clean-room builds from newly cloned repositories. No Android device/emulator was connected; instrumented tests, lint and release builds were not run. JVM success does not establish physical AR accuracy, permission behavior, media-storage reliability or background-service behavior.

## Dependency download recovery

The first StatusSave attempt stopped before the test task because Maven Central returned HTTP 403 for `org.jetbrains.kotlin:kotlin-scripting-compiler-embeddable:2.0.21`. The missing artifact was retrieved from the exact official repository endpoint, checked against its published SHA-1 checksum, and restored to the local Gradle artifact cache before the successful retry. No application source, Gradle build script or repository endpoint was changed for that recovery.

## Documentation and publication checks

- Matched the three selected Google Play listings to the exact Gradle application IDs: `com.ilya.safarshots`, `com.ilya.rulivo` and `com.statusvideo.statussaver`.
- Cross-checked features, dependency usage, dependency construction, persistence, asynchronous work and Android APIs against source code.
- Checked relative Markdown links and HTML image sources against the files actually published in Git.
- Distinguished actual Android QA captures, published promotional screenshots and deterministic renderer-test output. Original assets were retained, and the index contains only the selected applications' previews.
- Reviewed newly added documentation and publish file lists for secrets and personal data. Local SDK configuration, signing material, build outputs, release bundles and IDE metadata were excluded. StatusSave publishes `gradle.properties.example` instead of its configured local properties file.
- Kept existing policy documents containing personal contact details out of the source publication, and removed personal home paths from selected engineering notes.
- Published existing application source without editing its behavior. MapShots includes the source changes already present in the working checkout; its prior Git history was preserved.

## Published source snapshots

The selected application repositories are public and use `main`. These commits identify the reviewed source snapshots:

- [MapShots · `2a46bd6`](https://github.com/ILYAPROKOFEV101/MapShots/commit/2a46bd6a7244cc0b9bfc830992dbcdeb5b36d518)
- [Rulivo · `2f4ca7f`](https://github.com/ILYAPROKOFEV101/Rulivo/commit/2f4ca7fca8ddb0f52747d2d283d3afad8fd576d7)
- [StatusSave · `5d3d79d`](https://github.com/ILYAPROKOFEV101/StatusSave/commit/5d3d79d20f13f1b5df303c761a71c8e64b5bda4b)

Device-dependent limitations remain documented in each application README. Optional external SDK behavior was not established by JVM checks.
