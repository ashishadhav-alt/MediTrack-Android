# MediTrack Android app project

This project wraps your existing MediTrack website in an Android WebView and uses Android's native AlarmManager + notifications for scheduled reminders. Your existing HTML/CSS layout and medicine-management logic are retained.

## Open and build
1. Install Android Studio (with Android SDK Platform 35) on a Windows, Mac, or Linux computer.
2. Extract this ZIP.
3. In Android Studio choose **Open** and select the `MediTrack_Android_Project` folder (the one containing `settings.gradle`).
4. Allow Gradle sync and install any SDK components Android Studio requests.
5. Connect an Android phone with USB debugging enabled, or create an emulator, then press **Run**.
6. To create an APK: **Build → Build Bundle(s) / APK(s) → Build APK(s)**. Android Studio shows the output path when finished.

## Enable reminders on the phone
1. Open MediTrack and add a medicine with one or more reminder times in 24-hour format, e.g. `08:00, 14:30, 20:00`.
2. Tap **Enable notifications** and allow notifications.
3. If Android asks for exact-alarm access, allow it for MediTrack. On some Android versions this is under Settings → Apps → Special app access → Alarms & reminders → MediTrack.
4. Keep the phone powered on. The app can be closed and reminders are scheduled by Android; after a device restart the app restores its saved alarms.

## Important behaviour and limits
- Reminder data stays locally on this phone in the app's WebView storage. It is not synchronized with your Netlify website or another phone.
- Android may delay alarms if exact-alarm access is not granted, and some manufacturers apply battery restrictions. Check the phone's battery/background settings if reminders are delayed.
- No app can deliver a notification while the phone is powered off. After it starts again, saved reminders are restored.
- The current version schedules recurring daily reminders. Editing or deleting a medicine updates its scheduled alarms the next time the app saves/synchronizes the list.
- The notification is a reminder only. Follow instructions from your healthcare professional; confirm expiry information with a pharmacist.

## Project structure
- `app/src/main/assets/` — your original MediTrack website files
- `MainActivity.java` — Android WebView and JavaScript bridge
- `ReminderScheduler.java` — creates/cancels daily alarms
- `ReminderReceiver.java` — displays reminder notifications and schedules the next day
- `BootReceiver.java` — restores alarms after reboot

## Privacy
This version stores medicine details on the device. It does not upload them to a server. Keep your phone protected with its normal screen lock and do not share exported backups publicly.
