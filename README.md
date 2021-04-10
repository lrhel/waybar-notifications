# waybar-notifications

## Disclaimer

Copyright © 2021 Hel

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## Dependencies:
 - Daemonize
 - dbus-python
 - PyGObject
This script is an org.freedesktop.Notifications implementation that serve as simple notification system for Waybar using DBus. It allows an user to listen to org.freedesktop.Notifications Session Bus and create a /tmp/notifications file with the the latest notification in JSON format to use with Waybar. It can own the System Bus and act as a Session to System Bus Proxy to let other users send Notifications over the System Bus (useful in case of an user-sandboxed application).

## Usage:

To run as Session DBus
```
./waybar-notifications -u -d
```
To run as System DBus:
```
./waybar-notifications -s -d
```
NOTE: A proxy between the user's Session DBus and System DBus is initialized.

To run as proxy:
```
./waybar-notifications -p -d
```

Help message:
```
./waybar-notifications -h
```

## Waybar config:

Add this as Custom Module in your waybar configuration file:
```json
  "custom/notification": {
    "exec": "cat '/tmp/notifications'",
    "interval": 1,
	  "return-type": "json",
	  "max-length": 50
  }
```
