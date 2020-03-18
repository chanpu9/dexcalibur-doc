Latest news can be found here.

## 02 December 2019 - New feature : auto save

Did you never be afraid to lost your work when Dexcalibur crashes/exits ? Actually, a backup mechanism already exists, however you need to go into Setting -> Save menu, so it can be boring...   

New feature "Auto-save" allows you to automatically backup (into a file) Dexcalibur changes such as hook status, hook code, and aliases, when these are modified. At next Dexcalibur start, backuped data will be automatically restored.

![Auto-save status](https://raw.githubusercontent.com/FrenchYeti/dexcalibur-doc/master/pictures/autosave_status_on.png)

You can turn ON/OFF  auto-save by clicking on corresponding switch at right of navbar.

![Auto-save status](https://raw.githubusercontent.com/FrenchYeti/dexcalibur-doc/master/pictures/autosave_status_off.png)

Auto-save backup data into a file when :
* you **change hook code and click "save"** or "save & reply" from hook editor
* you **enable/disable a hook** from its on/off button
* you **rename a class/method/field**

 Link:
[https://github.com/FrenchYeti/dexcalibur/releases/tag/V0.6.1](https://github.com/FrenchYeti/dexcalibur/releases/tag/V0.6.1)



## 06 November 2019 - Release v0.6 + Major update

Latest version comes with lot of new features and changes.

New features:
- Hook editor helpers: the hook editor embeds a navigation bar of hook snippets for Java and native hooks.
- Polymorphic hook: static value into hook code can filled/updater automatically with data from previous application+hook execution. Allowing to do evolutive black-list.
- [Partial] Dynamic hook loading: when a method is hooked, the condition to load/unload hook can be defined. Now, you can configure from UI a hook to deploy only if a condition is verified at runtime. 
- All hooks can be enabled/disabled by a single click.
- Execution can be launch from hooking dashboard, so hook messages from previous execution are flushed before to display hook logs page.

Fix:
- Device Manager has been partially rewritten to be more stable. Default device where hooks should be deployed can be selected.
- Save/Open feature has been patched and UI redesigned.
- "Delete hook" works again.

Changes:
- Migration to Bootstrap 4
- UI theme
- Remote errors are now partially rendered client-side 
- UI is more compact, so more data can be displayed into a screen.
- Navigation bar has been rewritten to offer fastest access to features/inspectors
- 


## 07 July 2019 - New feature : "just-in-time decompilation" is available :)

One of the main features of Dexcalibur have been implemented : "just-in-time decompilation". Dexcalibur hooks DexClassLoader constructor in order to detect dynamic loading of additional Dex file, potentially deciphered at runtime. Then, when new bytecode chunk is detected, the chunk is sent back to the server, it is decompiled and the internal database (graph) is updated with discovered elements such as packages, classes, methods, fields, strings, byte array, and so.

The picture below shows the smali code of a function defined into a Dex file deciphered from a JNI library and loaded dynamically. Here, it is a crackme application and the static string is the flag. 


![JITD](https://raw.githubusercontent.com/FrenchYeti/dexcalibur-doc/master/pictures/JITD_v1_flag.png)

Freshly discovered classes can be explored and its methods hooked :)
![JITD](https://raw.githubusercontent.com/FrenchYeti/dexcalibur-doc/master/pictures/JITD_v1_class.png)
 

 

## 26 June 2019 - UI Improvements : fields setter/getter

The views and queries involving cross references have been improved. The information is more accessible for API user : **Field** have now *getters* and *setters* properties.


The UI have been improved in order to display getters and setters. You can get xref for a field from the Class  view.


![Xrefs of a field](https://raw.githubusercontent.com/FrenchYeti/dexcalibur-doc/master/pictures/gsetter_field.png)  


![Explore fields from a class](https://raw.githubusercontent.com/FrenchYeti/dexcalibur-doc/master/pictures/field_xref.png)  


When you search where a given symbol is referenced, if this symbol is a field, you can see if the instruction referencing this field sets or gets the value. 

![Results of searching call or use of a symbol](https://raw.githubusercontent.com/FrenchYeti/dexcalibur-doc/master/pictures/find_call_setget_field.png)  

## 25 June 2019 - Dexcalibur dockerfile improvements

I patch a long term issue : frida cli was not installed -_-"
The PATH env variable is now more complete, so you don't need to know the absolute path of ADB or Frida tools.

Theorically, the docker images contain the same major version of frida and node-frida, so there is probably lesser issue than a fresh install of Dexcalibur with an existing frida cli/server setup.
    

## 23 June 2019 - New inspector : Issue Inspector

Actually, this inspector catch the call to the SecurityException constructor and tags resulting logs as "Error". It is usefull in order to catch permission issue without use "adb logcat".



  