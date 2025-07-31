# MacOSX Launch App From WebLink

## Project Purpose
This project demonstrates how to create a macOS application that can be launched from web links. Through custom URL Schemes (such as `myprotocol://`), when users click on special links in web pages, it can automatically launch the specified macOS application.

## Technical Principle
Utilizes macOS's URL Scheme mechanism. When the system detects a URL with a specific protocol, it automatically launches the application registered for that protocol.

## Implementation Method

### References
- Reference 1: http://www.macosxautomation.com/applescript/linktrigger/
- Reference 2: http://hublog.hubmed.org/archives/001154.html

### Steps
1. Use Platypus to create `test.app`
2. Place `test.app` in the `/Applications/` folder
3. Add URL Scheme configuration to `Info.plist`

### File Structure
```
test.app/
└── Contents/
    ├── Info.plist
    ├── MacOS/
    │   └── test
    └── Resources/
        ├── AppSettings.plist
        ├── MainMenu.nib
        ├── appIcon.icns
        └── script
```

### Key Configuration
Add the following configuration to `Info.plist`:

```xml
<key>CFBundleURLTypes</key>
<array>
   <dict>
       <key>CFBundleURLName</key>
       <string>My Protocol</string>
       <key>CFBundleURLSchemes</key>
       <array>
           <string>myprotocol</string>
       </array>
   </dict>
</array>
<key>NSUIElement</key>
<true/>
```

- `CFBundleURLSchemes`: Defines the custom protocol name (in this example: `myprotocol`)
- `NSUIElement`: Set to `true` to run the application in the background without appearing in the Dock

## Usage

### 1. Create Application
Use Platypus tool to create the application based on the `test.platypus` configuration file.

### 2. Test Web Page
Open the `test.html` file and click the link inside:
```html
<a href='myprotocol://.'>test</a>
```

### 3. Execution Flow
1. Click the `myprotocol://` link in the web page
2. macOS system automatically recognizes the protocol and launches the corresponding application
3. The application executes the default script actions

## File Description

- `test.html`: Test web page containing links that trigger custom protocols
- `test.platypus`: Platypus project configuration file
- `test.sh`: Execution script (can customize application behavior when launched)
- `test.app/`: Final generated macOS application

## Notes

1. The application must be placed in the `/Applications/` directory to be properly recognized by the system
2. If using `window.open` to open links, remember to add the `window.open("", "_self")` parameter
3. Setting `NSUIElement` to `true` allows the application to run in the background, suitable for this type of utility tool

## Use Cases

- Quickly launch local applications from web pages
- Create a bridge mechanism between web pages and desktop applications
- Implement one-click installation or configuration features
