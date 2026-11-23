# Build MediTrack APK with GitHub Actions (no Android Studio)

This project includes `.github/workflows/android-build.yml`. GitHub Actions builds the debug APK in a cloud runner, so Android Studio does not need to be installed on your Windows laptop.

## Upload the project to GitHub

1. Sign in at https://github.com/ and create a new repository, for example `MediTrack-Android`.
2. For privacy, choose **Private**. Do not upload real medicine records, passwords, API keys, or personal data.
3. Extract `MediTrack_Android_Project.zip` on Windows.
4. Open the extracted `MediTrack_Android_Project` folder. Upload its contents to the repository root (the root must directly contain `settings.gradle`, `build.gradle`, `app/`, `gradle.properties`, and `.github/`). Do not upload only the outer folder as a nested directory.
5. If the browser upload does not include the `.github` folder, create a new file in GitHub named `.github/workflows/android-build.yml` and paste the workflow file included in this project.
6. Commit the files to the `main` branch.

## Download the APK

1. Open the repository's **Actions** tab.
2. Select **Build MediTrack Android APK** and open the latest run.
3. Wait until the build finishes. A green check means the workflow completed successfully.
4. In the run page, scroll to **Artifacts** and download `MediTrack-debug-apk`.
5. Extract the downloaded artifact ZIP. It contains `app-debug.apk`.
6. Transfer `app-debug.apk` to your Android phone and open it to install. Android may ask you to allow installation from the app you used to open the APK; only allow this for the APK you built and trust.

## Run another build

After changing project files, commit and push them to `main`; the workflow runs automatically. You can also use **Actions → Build MediTrack Android APK → Run workflow**.

## Notes

- This produces a **debug APK** for testing and personal installation, not a signed Play Store release.
- GitHub-hosted runners download Java, Gradle, and Android SDK components during the build, so the first run may take several minutes.
- If the workflow fails, open the failed job and read the first red step. Share the error text or screenshot so it can be diagnosed.
- Medicine information in this app is stored locally on the device by this project; it is not synced to your Netlify website.
