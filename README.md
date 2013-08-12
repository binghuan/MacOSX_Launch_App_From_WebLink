# MEMO

<pre>
Reference 1. http://www.macosxautomation.com/applescript/linktrigger/
Reference 2. http://hublog.hubmed.org/archives/001154.html
Following method by using reference 2. 
Use Platypus to create a test.app.
Then, put the test.app into folder "/Applications/"


The file hierarchy will be like this:
BH_MacBookPro:test.app binghuan$ tree
.
└── Contents
   ├── Info.plist
   ├── MacOS
   │   └── test
   └── Resources
       ├── AppSettings.plist
       ├── MainMenu.nib
       ├── appIcon.icns
       └── script


finally, add following key into Info.plist, that's it.

<key>CFBundleURLTypes</key>
<array>
   <dict>
       <key>CFBundleURLName</key>
       <string>Local File</string>
       <key>CFBundleURLSchemes</key>
       <array>
           <string>local</string>
       </array>
   </dict>
</array>
<key>NSUIElement</key>
<true/>

</pre>