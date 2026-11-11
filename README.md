# Discord Rust Android (starter)

An Android starter project for a **supported Discord bot client**. It uses a native
Jetpack Compose UI and a Rust core library. It does not log in as a normal Discord
user, automate a user account, or access private user DMs.

## What this starter does
- Lets you enter a Discord **bot token**.
- Calls Discord's supported `GET /users/@me` endpoint to verify the bot token.
- Passes the response through the Rust core for parsing and display.
- Keeps the token in memory only; it is not written to disk.

## Important limitations
A bot token represents a bot, not your personal Discord account. Bots can only see
and act in servers where they have been added, subject to their permissions and
intents. This starter is not a replacement for the official Discord mobile app and
does not provide personal-account login, personal DMs, or your normal account's
server list.

Do not paste your personal Discord password or user token into this app. Never
commit a bot token to source control or share it.

## Build using GitHub Actions (no local build tools needed)
1. Create a new GitHub repository.
2. Upload the contents of this project ZIP to the repository root (including the hidden `.github` folder).
3. Open the repository's **Actions** tab.
4. Select **Build Android APK**, then **Run workflow**. A push to `main` also triggers a build.
5. When the run finishes, open it and download the `discord-rust-android-debug` artifact.

The workflow installs Java, Android SDK/NDK, Rust and Gradle, builds the Rust native
libraries, then builds and uploads the debug APK. You do not need Android Studio,
Rust, or Gradle installed on your own device.

## Discord bot setup
1. Create an application in the Discord Developer Portal.
2. Add a bot to the application and copy its bot token.
3. Add the bot to a test server with only the permissions it needs.
4. Paste the bot token into the app's token field and select **Verify bot**.

The token is sensitive. If it is exposed, reset it in the Developer Portal.

## Project structure
- `app/` — Android application and Compose UI.
- `rust-core/` — Rust JNI library for parsing API responses.
- `scripts/` — helper script for building Rust native libraries.
