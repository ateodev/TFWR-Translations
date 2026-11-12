# Copies with Shortcuts
The Shortcuts app can copy your saves to a place you choose, such as iCloud Drive, each time you leave the game. It does this on its own, without asking. This is part of the full game.

## Set it up
1. In **Shortcuts**, tap + to make a new shortcut, tap **Edit** at the top right and add the game's action **Get latest save**.
2. Add **Save File** and tap its arrow. Turn off **Ask Where To Save**, choose a folder and turn on **Overwrite If File Exists**.
3. Tap **Search** at the bottom, then **Automation**, and under **Apps** choose **App**.
4. In the line that appears, tap **App** and choose the game, then tap **Opened** and choose **Closed**.

Before iOS 27, make the automation in the **Automation** tab instead: choose **App**, the game, only **Is Closed** and **Run Immediately**, then give it the actions of steps 1 and 2. On iOS 16, turn off **Ask Before Running** in its place.

Each copy is a zip named after its save, so you keep one current copy of each save.

## Keep older copies
Put the **Current Date** variable in the folder path of **Save File**. Copies made on another date then go to a folder of their own, and the older ones stay.

## More actions
**Get save** gets one save by its name. **Get saves** gets every save, or only those changed since a date.

## Bring a copy back
The actions only copy your saves out. To bring a copy back, press 'Import' on the load screen and choose its zip.

Cloud save keeps your devices on the same progress. A copy from Shortcuts is your own file, kept where you choose, for history or for the PC game.
