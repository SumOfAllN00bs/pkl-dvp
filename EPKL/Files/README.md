WARNING: HARD HAT AREA!
=======================

EPiKaL PKL is a Work-In-Progress, so all of it may not be working perfectly ... yet. ;-)

This is the EPKL Work-In-Progress README, going into details on the changes. For the normal EPKL README see the main folder.

~ Øystein B "DreymaR" Gadmar, 2020


DONE:
-----

**GENERAL/SETTINGS**
* Renamings and file mergings to make the code more compact and streamlined.
* Removed MenuIcons and HashTables code, replacing them with AHK v1.1+ native code.
* Unicode native AHK now works. SendU and changeNonASCIIMode removed.
* New iniRead functions that support the UTF-8 Unicode file format.
  
* Merged several .ini sections including eD specific ones into the default [pkl] as it's tidier.
* Made a PKL_Tables.ini file for info tables that were formerly internal. This way, the user can make additions as necessary.
* If using a layout from the command line, the notation "UseLayPos_#" will run layout # in the layout list set in EPKL_Layouts.
	- This also makes Refresh robust against layout changes in EPKL_Layouts.
* Base layout: Specify in layout.ini a basis file (layout section only). Just need to list changes in layout.ini now. Nice for variants.
* Shorthand notation in EPKL .ini layouts, allowing the KbdType/CurlMod/ErgoMod settings to be referred to as @K/@C/@E resp. (@V for all at once).
* Path shortcut for layout.ini entries, allowing ".\" instead of full path from EPKL root.
  
**MENUS/IMAGES**
* Edited menus and the About... dialog.
* Added a KeyHistory shortcut for debugging etc. Make it configurable in EPKL_Settings.ini (eD_DebugInfo).
* Added a Refresh hotkey. Reruns EPKL in case something got stuck or similar.
* You can specify in EPKL_Settings.ini which tray menu item is the default (i.e., activated by double-clicking the tray icon)
* Would tray menu shortcuts work? E.g., &About. Answer: The menu shows it, but unselectable by key(?).

* Multilayered help images so fingering can be in one image and letters/symbols in another (saves file space, adds options).
	- Shift/AltGr indicators on separate images in a specified directory instead of in the state#.png (and dk) images.
	- Allow pushing the help image horizontally if mouse x pos. is in the R/L ~20% zone.
	- Zoom and Move hotkeys for the help image, cycling between image sizes and positions. Set e.g., imgZoom = 60,100,150 (%) in EPKL_Settings.
	- Settings in layout.ini: Size/scaling, background/extend images, background color, shift indicator, icons and dead key dirs.
	- Settings in settings.ini: Overall transparency/opacity, top/bottom gutter distances, horizonal activation zone.
	- If settings are missing, may default to backgr.png, extend.png, on/off.ico and ModStateImg\ in the layout dir.
	- Instead of many lines of image sizes, introduced a scaling factor 'img_scale' (in percent).
* Help Image Generator, using my KLD format in an SVG image template. With search/replace this is turned into a key glyph image.
	- You'll need an Inkscape (Scalable Vector Graphics program) install. A good option is portable Inkscape from PortableApps.com.
	- You can choose whether to make shift state images only or a full image set with all shift states for all deadkeys. The latter takes time!
	- The HIG can be used from the menu when Advanced Mode is set. Its settings file is in Files\ImgGenerator.
	- In the HIG settings file you can control replacement characters used in a marking layer; anything written to it will show in bold yellow.
	- The SVG image template file is in the same location. You could use another template and specify it in the HIG settings file.
	- If you don't want the dead keys marked in yellow for instance, you could save the SVG template with that layer hidden.
	- You can make full layout images showing keys as well, by combining with a Files\ImgBackground image of choice. I use the GIMP for that.
  
**MAPPINGS**
* Updated and added several layouts, including locale and script variants.
* Removed explicit Cut/Copy/Paste keys (in pkl_keypress.ahk); use +{Del} / ^{Ins} / +{Ins} (or as I have used in my Extend mappings, }^{X/C/V ).
* Made an _eD_Extend.ini file for Extend mappings that were formerly in pkl.ini (or layout.ini). The old way should still work though.
* Made Extend substitutes for Launch_Media/Search/App1/App2, as AHK multimedia launcher keys aren't working in Win 10.
* Scan code modular remapping, making ergo and other variants much easier. Separate key permutation cycles, and remaps combining/translating them.
	- In layout.ini, specify any remap combinations using the names (and syntax) found in the [remaps] section of the Remap.ini file.
	- The _layout remap specifies a full remapping, while the _extend remap is only for those keys you want to move for Extend ("hard" remaps).
	- Uses my KeyLayoutDefinition (KLD) mapping format.
	- KLD is good for remaps, but too compact for main layout or Extend definitions. (Besides, Aldo Gunsing has a conversion tool for those.)
	- Unfortunately though, I can't make that work for the help images directly. New images need to be generated then.
	- Should I have a cycle merge syntax, e.g., "Angle_ISO105 = TC<  |L0LG  | ^Angle_ANSI-Z"? Probably unnecessary.
* Virtual Key remapping, similarly to SC. I'd like to make only ANSI or ISO layouts, and leave the ISO-ANSI VK issue to a simple remap routine.
* Sensible dead key names for images and entries (e.g., @14 -> tilde) in a central doc that layouts can point to.
	- Dead key list and file path in layout (but use dk## in the layout itself, for compatibility!)
	- If no lookup is specified, EPKL defaults to the local file as before
	- This way, one change in a DK will affect all layouts using that DK
	- DK images may still be kept in the layout dir (or a subdir to avoid clutter), as they are layout dependent
	- DK imgs named ‹name›_dk‹#› for state ‹#› (add s6/7 where applicable?!)
* Greek layout w/ tonos/dialytika in the acute/umlaut dead keys.
* In the OS deadkey table ([DeadKeysFromLocID] in PKL_Tables.ini) a -2 entry means no dead keys and RAlt may be used as AltGr (altGrEqualsAltCtrl).
* Special keys such as Back/Del/Esc/F# used to release a dead key's base char and also do their normal action. Now they just cancel the dead key(s).
* A single layout entry of VK or -1 will set that key to itself as a VirtualKey (if it was set in the base layout and you don't want it remapped).
  
**OTHER/NOTES**
* There was a problem with DKs getting stuck after a special entry. Seems this was always the case?! A call to pkl_Send(0) somehow prevents it...
  
**PKL[eD] VERSION INFO**
* PKL[eD] v0.4.5: Literals/Ligatures/Powerstrings specified by the '&‹entry›' syntax for layouts/Extend/deadkey entries. Can be defined as multiline.
	- There's a string file specified in the layout.ini, by default it's Files\_eD_PwrStrings.ini
	- The ligature name can be any text string. In layout entries, two-digit names are prettiest.
	- Note that programs handle line breaks differently! In some apps, \r\n is needed but that creates a double break in others.
	- SendMode can be selected for powerstrings (Input, Message, Paste from Clipboard) in the string file.
	- To avoid stuck modifiers for long strings, a SendMessage() method was implemented.
	- More generic dead key output: Same prefix-entry syntax as layout/Extend, parsing "%$*=@&" entries.
		- Dead key base/release entries can be in 0x#### Unicode format in addition to the old decimal format. For base keys, the syntax must be exact.
		- Examples: "102 = ƒ" is possible instead of "102 = 402". For a glyph not shown in your font such as Meng, "77 = 0x2C6E" (or 11374 still).
		- Should be easy to import MSKLC dead key tables of the form '006e	0144	// n -> ń' by script (e.g., RegExp "0x$1 = 0x$2	; $3")
* PKL[eD] v0.4.6: The base layout can hold default settings. Layout entries are now any-whitespace delimited.
	- pklIniRead() can have an altFile, such as "BasIni". For BasIni/LayIni, .\ and ..\ point to their own and mother directories.
	- Read most layout settings apart from remaps from the base layout if not found in the main layout.
	- ONHOLD: Look for backup bgImg/extImg/dkImg in BasIni after all? If using an ANS base file for an ISO layout, it looks silly. But better than nothing?
	- Requiring Tab delimited layout entries was too harsh. Now, any combination of Space/Tab is allowed. For Space, use ={Space}.
* PKL[eD] v0.4.7: Multi-Extend w/ 4 layers selectable by modifiers+Ext. Extend-tap-release. One-shot Extend layers.
	- Multi-Extend, allowing one Extend key with 2 modifiers (e.g., RAlt/RShift) to select up to 4 different layers. Ext+Mod{2/3/2+3} -> Ext2/3/4.
	- Ext2 is a NumPad/nav layer w/ some useful symbols. Ext3/Ext4 are one-shot string layers but mostly to be filled by the user.
	- Dual-role tap-release Extend key. Works as Back on tap within a certain time and Ext on hold. Set the time to 0 ms to disable it.
	- ExtReturnTo setting to allow one-shot Extend, e.g., for strings. Can for instance return from Ext3 to Ext1.
* PKL[eD] v0.4.8: Sticky/One-shot modifiers. Tap the modifier(s), then within a certain time hit the key to modify.
	- Settings for which keys are OSM and the wait time. Stacking OSMs works (e.g., tap RShift, RCtrl, Left).
	- NOTE: Mapping LCtrl or RAlt as a Modifier causes trouble w/ AltGr. So they shouldn't be used as sticky mods or w/ Extend if using AltGr.
	- Powerstrings can have prefix-entry syntax too now. Lets you, e.g., have long AHK command strings referenced by name tags in layouts.
  
**EPKL VERSION INFO**
* EPKL v1.0.0: Name change to EPiKaL PKL. ./PKL_eD -> ./Files folder. Languages are now under Files.
	- Bugfix: A '--' entry in layout.ini didn't overwrite the corresponding BaseLayout.ini entry.
* EPKL v1.1.0: Some layout format changes. Minor fixes/additions. And kaomoji!  d( ^◇^)b
	- Fixed: DK images were gone due to an error in EPKL_Settings.ini. DK images also didn't work for some layouts.
	- Fixed: Sticky/One-Shot mods stayed active when selecting Extend, affecting strings if sent within the OSM timer even when sent with %.
	- New: A set of Kaomoji text faces in the Strings Extend layer. Help images included.  ♪～└[∵┌]└[･▥･]┘[┐∵]┘～♪
	- New: Hungarian Cmk[eD] locale variant.
	- New: Zoom and Move hotkeys for the help image, cycling between image sizes and positions. Set e.g., imgZoom = 60,100,150 (%) in EPKL_Settings.
	- Tutorial on making a layout variant in README. How to make and activate a layout, changing locale, remaps and a keys mappings.
	- Moved the BaseLayout files up one tree level. In layout.ini, use its file path from Layouts w/o extension, e.g., Colemak-VK\BaseLayout_Cmk-VK-ISO
	- 'Spc' and 'Tab' layout mappings, sending {Blind}{Key}. Makes for compact layout entries for the delimiting whitespace characters.
	- Direct Extend key mapping, e.g., for CapsLock use 'SC03A = Extend Modifier' rather than the extend_key setting with a mapped key as before.
	- Extend layers can be set as hard/soft in the _Extend file. Soft layers follow mnemonic letter mappings, hard ones are positional (like my Ext1/2).
		- The Curl(DH) Ext+V may still be mnemonic/soft instead of positional/hard (^V on Ext+D). Use _ExtDV with AWide/Angle mods for mapSC_extend then.
* EPKL v1.1.1: Some format changes. Minor fixes/additions. Tap-or-Mod keys (WIP).
	- Fixed: HIG made a state8 image of semicolons. This was due to the SGCaps states (8:9) being added unnecessarily.  (つ_〃*)
		- Also fixed some minor HIG bugs related to hex dead key values etc.
	- New: Tap-or-Modifier a.k.a. Dual-Role Modifier keys. Work-in-progress, not working well for rapidly typed keys yet.
		- To make a ToM key, specify its VK layout entry as VK/Mod, where 'Mod' is a modifier name. The rest of the line can be any valid entry.
		- The Help Image Generator can mark ToM keys (state 0 and 1) with a background symbol.
	- The Extend key can be set the old way as extend_key in [pkl] (but no layout entry is needed anymore!), as 'Ext Mod' or as ToM, e.g., 'VK/EXT VKey'
	- Modifiers can be referred to by the first letters of their name so, e.g., 'LS' and 'LSh' both point to LShift. Also, VK or VKey = VirtualKey.
	- Unicode points can be sent by the ~ prefix; a ~#### entry sends the U+#### character as used in MSKLC file entries.
	- The shiftStates layout entry is now in the [layouts] section of layout.ini, spaced out so entries have more room and are clearer.
	- Instead of the special Spc and Tab entries, use &Spc and &Tab, defined in the PowerStrings file.
	- Dead key abbreviations are now by code point instead of numbered, as in MSKLC. Example: The .klc entry 02c7@ is a caron DK; in EPKL it becomes @2c7.
	- Added a Compile_EPKL.bat file that compiles the source code by running AHK2Exe with default settings.
* EPKL v1.1.2: Multifunction Tap-or-Mod Extend with dead keys on tap. Janitor inactivity timer.
	- The EPKL.exe binary file is no longer version controlled. It can be compiled using the .bat file but is also provided with each release.
	- Dead keys on Extend key tap. Examples: Tap {Extend, n} for parentheses with positioning. {Ext, z/Z} Undo/Redo. {Shift, Ext, letter} for kaomoji.
	- Sticky Shift works to select Extend dead keys, and stays active. If you want the shift-P kaomoji tap {Shift, Ext} then P quickly. If not, wait.
	- IniRead can now handle UTF-8 .ini files (but not UTF-16) allowing Unicode in all entries.
	- For InputRaw/Send/AHK/Blind/Unicode/DeadKey/PowerString entry prefixes, both the old %$*=~@& or →§αβ«Ð¶ (AltGr+Shift+ISABUDP) work now.
	- Direct dead key entries in the format <#> = <entry> work too. If the char is an uppercase version, append a plus (<#>+).
	- "Janitor" inactivity timeout setting (e.g., 2 s) to release any stuck modifiers. These can happen with advanced usage.
* EPKL v1.1.3: The LayStack, separating & overriding layout settings. Bugfixes. More kaomoji.
	- The downloadable release asset .zip file now contains all files needed to run EPKL. No Source/Other/Data nor .bat/.git. files.
	- The Kaomoji dead key now outshines the Extend layer with a related entry for each shifted letter/symbol, e.g., d( ^◇^)b vs (b￣◇￣)b.
	- An EPKL_Layouts_Default .ini file has been split off from EPKL_Settings.ini so the layout definitions have a file of their own.
	- If present, an EPKL_Layouts_Override.ini file will take precedence. In the future, this may be generated by a GUI panel.
	- Several mappings and settings common to most layouts are now in the Layouts_Default file. This includes the Extend modifier mapping.
	- The LayStack [ mainLay, baseLay, LayOver, LayDef ] can be used for most mappings and layout info, including Extend and DeadKey overrides.
	- Added Layout Type (eD or VK) and Other Mod (e.g., Sym) shortcuts to the Layouts.ini file.
	- The 'Sym' (;>' />=>- cycles) symbol key rotation mod I'm testing is available as a remap.
	- The CurlM/DHm variant of the Curl(DH) mod is available through the remap 'Curl-DHmMod'; it isn't available for most premade layouts though.
	- Added eD/VK Colemak Curl(DHm) only layouts. Used CurlM/DHm here, to support ortho boards. Ortho help images are on the TODO list.
	- Fixed: The Extend modifier in the BaseLayout didn't work so most layouts didn't get Extend before adding it to their layout.ini manually.
	- Fixed: From PKL[eD] v0-4-5, DK+Spc didn't release the base accent as Spc was prefixed. Now, (&)Spc and {Space} are turned into a space glyph.
	- Fixed: Some kaomoji with ^ or ` in them would get confused - (=･ω･^^=)丿 - due to insufficient handling of OS dead keys.
	- Fixed: Ensured that a quickly used Extend press isn't open for re-use as an Extend tap! Example: Ext+Space, then quickly E.
	- Fixed: The janitor timer kept resending mod up strokes every # s. Now it's once only after recent keyboard activity.
	- Minor: Made a bool() fn to use bool(pklIniRead()) instead of a dedicated pklIniBool().
	- Tested: The LAlt key (SC038) can work as Extend Modifier, just like any other key can. (Remapping another key to LAlt can still be tricky.)


TODO:
-----

* Dead key chaining (one DK may release another). EPKL allows the @## syntax but it doesn't work as it should yet. Because it resets PVDK?

* Check whether Ralt (SC138 without LCtrl) will be AltGr consistently in layouts with state 6-7.

* Add to unmapped dead key functionality
	- Specify release for unmapped sequences. Today's practice of leaving an accent then the next character is often bad.
	- That way, one could for instance use the Vietnamese Telex method with aou dead keys (aw ow uw make â ô ư) etc.
	- One catch would be that the dead key wouldn't release until next key press, but that may be acceptable.
	- Specify, e.g., the entry for s1 similar to today's s0 entry. (U+0000–U+001F are just ‹control› chars.)
	- That'd be backwards compatible with existing PKL tables, and one can choose behavior.

* Truly transparent image background without the image frame. Overall transparency (but not transparent color?) works.
	- Transparent foreground images for all states and dead keys.

* Some more dead key mappings:
	- Greek polytonic accents? Need nestable accents, e.g., iota with diaeresis and tonos. See https://en.wikipedia.org/wiki/Greek_diacritics for tables.
	- Kyrillic special letters like ёЁ (for Bulmak) җ ӆ ҭ ң қ ӎ (tailed); see the Rulemak topic
	- IPA on AltGr+Shift symbol keys?

* Define Mirror layouts as remap cycles?
	- Should be able to mirror any layout then?
	- Make sure to apply mirroring last?

* Option to have layouts on the main menu like vVv has: "Layout submenu if more than..." setting?


INFO: Some documentation notes
------------------------------

* Virtual key code links:
    http://www.kbdedit.com/manual/low_level_vk_list.html
    https://msdn.microsoft.com/en-us/library/ms927178.aspx
    https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731(v=vs.85).aspx
  
* "Anti-madness tips" for EPKL (by user Eraicos and me):
    - PKL using AHK v1.0: Script files need to be ANSI encoded. They don't support special letters well.
        - EPKL using AHK v1.1-Unicode: Supports scripts in UTF-8 w/ BOM.
    - EPKL .ini files may be UTF-8 encoded, with or without BOM. Source .ahk files should be UTF-8-BOM?
        - PKL: Don't use end-of-line comments in the .ini files. OK in layout.ini because of tab parsing.
        - EPKL: End-of-line comments are now safe.
    - In layout.ini, for old PKL:
        - Always use single tabs as separators in layout.ini, also between a VK code and 'VirtualKey'.
        - The CapsLock key should have scan code 'CapsLock' instead of SC03A, if using 'extend_key = CapsLock'.
        - The Extend key should be mapped or it won't work, e.g., 'CapsLock = CAPITAL	VirtualKey'.
        - EPKL changes all of the above: Any whitespace delimits, and Extend is mapped as 'Extend Modifier'.
    - In the Extend section:
        - Don't have empty mappings in the Extend section. Comment these out.
        - By default {} is added to send keys by name. To escape these, use a prefix-entry or }‹any string›{.
  

**Entry format info from Farkas' sample.ini layout file:** (Note that EPKL now uses '@' for 'dk' entries etc)
```
Scan code =
	Virtual key code (like in MS KLC)
	CapsState (like in MS KLC):
		If CapsState == vk or VirtualKey
			When you press this key, it sends only the virtual key.
			It is very useful, if you install your special layout, and you 
			would like to extend it. (See extend_* layouts)
		Else If CapsState == modifier
			You can use this key as a modifier, like Shift, RAlt (== AltGr)
		Else If CapsState & 1 (first bit set)
			Shift + Key == CapsLock + Key
		Else If CapsState & 4 (third bit set)
			AltGr + Shift + Key == CapsLock + AltGr + Key
	Output for each shift state (see http://www.autohotkey.com/docs/commands/Send.htm):
		#       send utf-8 characters (one or more)
		*####   send without {Raw} – that is, interpret key names (and ^+1#{} ?) in AHK style
		=####   send {Blind} – that is, keep the modifier state intact
		%####   utf ligature
		--      disabled key/state entry
		dk##    deadkey (EPKL: @## is used instead, w/ ## from a DeadKeyNames section)
		&###    EPKL: PowerString name (named strings that are sent by the chosen method)
NOTE: Use tabs as separator for these entries!!!

;scan = VK	CapStat	0Norm	1Sh	2Ctrl	6AGr	7AGrSh	Caps	CapsSh
SC002 = 1	1	1	!			; QWERTY 1!
SC003 = 2	0	2	={Left}		; QWERTY 2@
SC004 = 3	0	3	*{Right}	; QWERTY 3#
SC005 = rshift	modifier		; QWERTY 4$
SC006 = 5	0	dk1	dk2			; QWERTY 5% (EPKL: Use, e.g., @01 @02 for DKs)

[deadkey1]
; 0 = unicode number of the "accent"
0    =  126	; ~
; [Unicode number of the base letter] = [Unicode number of the new letter] ‹tab› ; comments
97   =  227	; a -> ã
```
