title: ''
author: ''
appears: ''
updated: Invalid date

---

## Gimp Tips

### Round Corners is Greyed Out

* **Problem:** Round corners tool is greyed out. This happens if the image has an alpha channel.
* **Solution:** Remove the alpha channel. Hit: Layers -> Transparency Layer -> Remove Transparency Layer. Rejoice.

## Windows Mobile Tips

### Windows Media Player for Windows Mobile (or PocketPC)

* **Problem:** My windows media player doesn't stream music or play videos properly ' the device or screen turns off after 1-2 minutes, and also turns off the media player. How do I fix this?
* **Solution:** Turns out that the problem is NOT a registry fix ' it's just that the actual evice is turning itself off (at a system level), and not just the screen (which is what you'd expect). To fix this, hit: Start > Settings > System > Power > Advanced. Uncheck the boxes that turn off your device after a timeout.

### Google Calendar and Windows Mobile Calendar Sync

I use OggSync to synchronize my Google Calendar with the calendar on my Windows Mobile device. Note that the freeware version only synchronizes one (your main) calendar on Google, and not the other calendars.

## Windows

* [Disable automatic restart after](http://tinyapps.org/blog/windows/201010160700_disable_windows_7_auto_restart.html) - add `NoAutoRebootWithLoggedOnUsers` DWORD value to `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU` and assign value data of `1` Windows 7 updates
