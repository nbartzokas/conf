## Basic launchd .plist configuration file

Great reference info here:

- [developer.apple.com](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man5/launchd.plist.5.html)
- [launchd.info](http://launchd.info/)

### Usage

Software runs differently depending on where you place the launchd .plist file:

- `~/Library/LaunchAgents/` launches an app as a user
- `~/Library/LaunchDaemons/` launches a service as a user
- `/Library/LaunchAgents/` launches an app as an admin
- `/Library/LaunchDaemons/` launches a service as an admin

### Configs

Label of the app. Every .plist on a machine needs a different Label. Multiple .plists with the same Label won't start.

    <key>Label</key>
    <string>com.COMPANY.APP</string>

Absolute path to the app.

    <key>Program</key>
    <string>/Applications/APP.app/Contents/MacOS/Electron</string>

To run at system boot. Alternatives are `StartInterval` and `StartCalendarInterval`.

    <key>RunAtLoad</key>
    <true/>

To restart the app on crash, but not on manual exit.
    
    <key>KeepAlive</key>
    <dict>
        <key>SuccessfulExit</key>
        <false/>
    </dict>

To output standard out and error to specific files. These files should be rotated.

    <key>StandardOutPath</key>
    <string>/tmp/com.COMPANY.APP.out.log</string>
    <key>StandardErrorPath</key>
    <string>/tmp/com.COMPANY.APP.err.log</string>

Avoid OSX backgrounding the app. For more info, see `ProcessType` at [developer.apple.com](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man5/launchd.plist.5.html).

    <key>ProcessType</key>
    <string>Interactive</string>

</dict>
</plist> 
