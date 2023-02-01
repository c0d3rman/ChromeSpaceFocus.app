# ChromeSpaceFocus.app

For some reason, in newer versions of MacOS, Chrome sometimes does not properly gain focus when switching spaces.
If you have multiple Chrome windows in fullscreen, and swipe from one to another, focus won't be shifted to the new window.
E.g. if you hit Command+T, the new tab will be created in the offscreen window you just came from.
You can regain focus by clicking anywhere in the new window, but it's extremely annoying. 

This app was created to solve that. It uses Applescript to continuously check for fullscreen Chrome windows on the screen and focus on them.
It's not a very elegant solution but it works.

The app runs in the background - when you open it, it will appear in the Dock for a moment before disappearing.
Because it runs in the background, there's no visible indication of when it's running. To see if it's running, go to Activity Monitor and search for `ChromeSpaceFocus`. You can also exit the app from there (by force quitting it). 

The app is extremely simple; you can see its entire code [here](https://github.com/c0d3rman/ChromeSpaceFocus.app/blob/main/Contents/MacOS/ChromeSpaceFocus) if you're worried about it doing anything fishy.

## Installation

1. Download this repository by cloning it or using [this link](https://github.com/c0d3rman/ChromeSpaceFocus.app/archive/refs/heads/main.zip) and unzipping.
2. Rename the folder `ChromeSpaceFocus.app` and confirm on the dialog box that appears.
3. Open the app. It will crash because it doesn't have Accessibility permissions, which it needs in order to trigger focus.
4. Go to System Preferences -> Privacy & Security -> Accessibility. You should see a new item there named `osascript` - this is Apple's name for the executable that runs Applescript code. Turn the switch next to it on.
5. Open the app again. This time it will work.

Optional steps:

6. Move the app to your `/Applications` folder for convenience.
7. Confirm that the app is running by going to Activity Monitor and searching for `ChromeSpaceFocus`.
8. Add the app to your Login Items so it starts automatically when you log in - go to System Preferences -> General -> Login Items and click the + in the "Open at Login" section, then choose `ChromeSpaceFocus.app`.

## Known issues

Feel free to submit PRs to fix any of these.

- Sometimes when swiping between spaces very fast, the app will pull you back to a previous space because it erroneously tries to focus on a space you've already moved on from.
- It's completely untested with multiple displays and probably won't work with multiple displays.
- The app does not display any crash message, so if it dies the user is unaware.
- It's very annoying to quit the app - it would be nice if it had an icon in the menu bar.
- The accessiblity permission in preferences shows as `osascript`; it would be nice if it could show as `ChromeSpaceFocus`.
- There's no logging.
- It's only tested on MacOS Ventura - it's unknown if it works on other versions.
- It'd be nice to give a simpler download link that downloads a `.app` directly.
