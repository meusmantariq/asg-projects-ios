# ASG Projects — iOS App

Native SwiftUI app that opens https://projects.alsaifgraphics.com/ in a full-screen WebView.

## This is a complete, buildable Xcode project
Unlike loose source files, this folder is structured exactly as Xcode expects
(`ASGProjectsApp.xcodeproj` + source folder + asset catalog), so it can be
built directly by Codemagic or Xcode without any extra setup steps.

## Build with Codemagic (no Mac needed)
1. Upload the entire contents of this folder to the root of your GitHub repo
   (drag-and-drop via "Add file > Upload files" on GitHub works fine — just
   make sure `ASGProjectsApp.xcodeproj`, `ASGProjectsApp/`, and
   `codemagic.yaml` all land at the repo root, not nested in a subfolder).
2. In Codemagic, connect the repo (you're already on that screen).
3. Codemagic will detect `codemagic.yaml` automatically and offer the
   "ASG Projects iOS Build" workflow.
4. Before running the build, go to your Codemagic app settings ->
   **Code signing identities** and connect your **Apple Developer account**
   (Codemagic can auto-generate certificates/profiles for you — this is the
   easiest option, look for "Automatic code signing" / "Apple Developer
   Portal integration").
5. Update `bundle_identifier` in `codemagic.yaml` if you want something other
   than `com.alsaifgraphics.projects` — it must be unique to your Apple
   Developer account.
6. Click **Start new build**. When it finishes, the `.ipa` is attached under
   **Artifacts** on the build page, and (if you keep the publishing block)
   emailed to itsupport@alsaifgraphics.com.

## Requirements you still need
- A free Codemagic account (works fine on their free tier for occasional builds).
- An **Apple Developer Program** account (US$99/year) — this is an Apple
  requirement for signing any iOS app, there's no way around it even with CI.
- Devices you want to install the `.ipa` on (for Ad Hoc distribution) need
  their UDIDs registered in your Apple Developer account — Codemagic can
  prompt for this during signing setup.

## Local build (if you ever get access to a Mac)
Just double-click `ASGProjectsApp.xcodeproj` to open in Xcode, pick your team
under Signing & Capabilities, then Product > Archive > Distribute App.
