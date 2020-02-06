DreymaR's Big Bag Of Keyboard Tricks - EPKL
===========================================

### [EPiKaL PortableKeyboardLayout][CmkPKL] for Windows, with layouts
#### ~ The original [PKL][PKLGit] written by [Farkas Máté in 2008][PKLSFo] using [AutoHotkey][PKLAHK]
#### ~ [EPKL][CmkPKL], formerly PKL[edition DreymaR] by DreymaR, 2017-

[Θώθ][ThothW] – What Is This?
-----------------------------

Info about DreymaR's Big Bag of keyboard trickery is mainly found on the Colemak forum:
* The [Big Bag main topic][CmkBBT] with better explanations and links.
* Daughter topics for implementations, including the [Big Bag for EPKL/Windows][CmkPKL] one.
  
* This repo implements most of my Big Bag for (E)PKL, as layout and other .ini files.
* It also contains **EPiKaL PKL** (**[EPKL][EPKLRM]**) with several improvements over PKL.
* Big thanks to Farkas Máté, the AutoHotkey people, Vortex(vVv) and all other contributors.

Getting EPKL up and running
---------------------------

* Download a full copy of this repo or just its executable resources.
    - Under [https://github.com/DreymaR/BigBagKbdTrixPKL/releases](Release) Assets, there's a .ZIP file with the files needed to run EPKL.
    - If you also want the source code, press the GitHub Download/Clone button and then unzip the file you got.
    - If you download or clone the repo, you need to run Compile_EPKL.bat to produce the EPKL.exe binary.
* **FAST LANE:** If you want "just Colemak" the simple way, then rename the EPKL_Layouts_Override.ini file so EPKL uses defaults.
    - Otherwise, see below for how to set and/or edit the layout(s) you want.
* Now, simply run EPKL.exe inside its main folder in any way you like!
* EPKL, being portable, doesn't need an install with admin rights to work. You must still be allowed to run programs.  
  
* I usually put a shortcut to EPKL.exe in my Start Menu "Startup" folder so it starts on logon, per user.
* EPKL can also easily be used with the [PortableApps.com][PrtApp] menu by putting its folder in a C:\PortableApps folder.
    - If the PortableApps menu is started on logon it can start up EPKL for you too.  
  
* Choose a layout with your ISO/ANS(I) keyboard type, locale and Curl/Angle/Wide preferences, by shorthand or full name.
    - There are two main layout types: VK which only moves your keys around, and eD which map each shift state for each key.
    - There are some premade Locale variants, if you need to type in other languages. Check out which variants exist.
* In your EPKL_Layouts .ini, activate the layout(s) you want by editing and/or uncommenting (remove initial semicolon).
    - There's a Layouts_Default and a Layouts_Override file. Entries in the override, if present, take precedence.
    - My shortcuts use the KbdType (@K) etc values but you could also type the path to a layout folder out in full
    - The format is: layout = ‹1st layout folder name›:‹name you want in menu›,‹2nd layout folder›:‹2nd menu entry› etc

More Know-How-To
----------------

* This repo contains executables for EPKL as well as the original PKL, and source code for both.
* The layouts are updated to EPKL format though, so they'd need some reconstruction for old PKL.
* The EPKL_Layouts .ini files hold layout choices. EPKL_Settings.ini holds general program settings.
* The layout.ini files hold layout settings and mappings. They often point to and augment a BaseLayout.ini file.
* There's a "LayStack" priority stack for layout info. Mappings/settings at higher levels will take precedence:
    1) The layout.ini file in the chosen Layout folder gets the last word about, e.g., remaps
    2) The BaseLayout.ini file usually found under each layout type may define most of the layout
    3) The EPKL_Layouts_Override, if present, can contain non-default info about the layout choice etc
    4) EPKL_Layouts_Default.ini, finally, holds default and common settings/mappings
    5) Beyond this, specialized files may hold Extend or DeadKey mappings. See below.
In theory, you could put all the info needed for a whole layout into any one of these "layout stack" files.
  
The files may take a little tweaking to get what you want. There are several parameters:
* Colemak vs QWERTY vs what-have-you, obviously. Choose wisely!
    - This repo by default contains mainly Colemak(-DH) and Tarmak layouts, with QWERTY included.
* Full/VK mappings: I've provided my own Colemak[eD] as well as 'VirtualKey' versions
    - The 'VK' layouts just move the keys of your installed OS layout around, without other changes
    - The [eD] layouts have their own Shift/AltGr mappings specified. You may mix types if you want.
* ISO (European/World) vs ANSI (US) vs other keyboard types
    - ISO boards have a `VK_102` key between `Z` and `LShift`. Some `OEM_` key codes differ from ANSI ones.
    - JIS (Japanese) etc are not supported so far - sorry.
* Curl(DH), Angle and/or Wide ergonomic mods, moving some keys to more comfortable positions
    - Angle/Wide affect the "hard" key positions in the layout.ini file, usually both for Layout and Extend
    - Curl(DH) is Colemak/Tarmak specific and for the most part should not affect Extend
* Extend mappings, using for instance CapsLock as a modifier for nav/edit/multimedia/etc keys. It's awesome!!!
    - The Extend modifier may even double as a Tap-or-Mod key so that when you tap it, something else happens.
    - The most advanced way of using this may be the Mother-of-DeadKeys which allows really fancy "tap dances"!
    - Holding down Shift and/or AltGr while first holding or while tapping the Ext key affects which layer is used.
* In EPKL_Layouts.ini you can use shorthand for KbdType/CurlMod/ErgoMod etc, or set the layout folder path directly.
    - For Extend set an Extend file and a working Extend modifier. The latter needs to be mapped to a key.
    - My Extend mappings file is in the Files folder. Look inside it to learn more.
* In the layout folder(s) you've chosen, you may edit the layout.ini files further if required. See below.
    - Mod remaps, help image specifications, Extend key, key mappings etc can be set in the LayStack .ini files.
    - Many layouts use a base layout. Most mappings may be there, so the top layout.ini only has to change a few keys.
* To learn more about remaps, see the _eD_Remap.ini file. They can even turn Colemak into QWERTY (oh no...!).
* There's a file for named literals/powerstrings. These are useable by layouts, Extend and dead keys.
* Also, a dead key file. DKs are mapped as @###. Pressing the key then a release glyph may produce something new!
    - There are help images for DKs, these can be very useful as they show what releases are in different shift states.
    - I haven't made images for all variants though, so there may be minor discrepancies.
* Help images aren't always available with the right ergo mod and keyboard type, since there are many combos. See below.
  
**Hotkeys found in the EPKL settings file:**
* Ctrl+Shift+1 – Display/hide help image
* Ctrl+Shift+2 – Switch layout between the ones specified in the settings file
* Ctrl+Shift+3 – Suspend EPKL; hit again to re-activate (it may be Ctrl+Shift+` instead)
* Ctrl+Shift+4 – Exit EPKL
* Ctrl+Shift+5 – Refresh EPKL, if it gets stuck or something
* Ctrl+Shift+6 – Zoom the help image in/out, to see it better or get it out of the way
* Ctrl+Shift+7 – Move the help image between positions, as by mouseover
  
**Techy tips for EPKL:**
* Look in the various .ini files under Files and Layouts if you're interested! Much is explained there.
* See my examples in the Extend file for some advanced mappings! These may be used in layouts and dead keys too.
* EPKL uses both .ini and source files that may be UTF-8 Unicode encoded.
* EPKL allows end-of-line comments (whitespace-semicolon) in .ini files, but the original PKL only allows them in layout entries.
* Running EPKL with other (AutoHotkey) key mapping scripts may get confusing if there is so-called _hook competition_.

Key mappings
------------

Most of my layouts have a base layout defined; their layout section may then change some keys. You can add key definitions following this pattern.
  
Here are some full key mappings followed by a legend:
```
SC018 = Y       1     y     Y     --    ›     »     ; QWERTY oO
SC019 = OEM_1   0     ;     :     --    @0a8  …     ; QWERTY pP - dk_umlaut (ANS/ISO_1/3)
;SC   = VK      CS    S0    S1    S2    S6    S7    ; comments
```
Where:
* SC & VK: [Scan code ("hard code")][SCMSDN] & Virtual Key Code [("key name")][VKCAHK]; also see my [Key Code Table][KeyTab].
    - For SC, you can use an AHK key name instead. For full mappings I think you need the real VK name in the VK entry.
    - _Example:_ The above SC are for the `O` and `P` keys; these are mapped to their Colemak equivalents `Y` and `;`.
    - Check out that the ISO/ANSI specific `OEM_#` key numbers are right for you, or remapped with a VK remap.
    - _Example:_ `OEM_1` above is the semicolon key for ANSI, but ISO names the semicolon key `OEM_3`.
    - If the VK entry is VK/ModName, that key is Tap-or-Mod. If tapped it works as stated, if held down it's the modifier.
    - The VK code may be an AHK key name. For modifiers you may use only the first letters, so LSh -> LShift etc.
* CS: Cap state. Default 0; +1 if S1 is the capitalized version of S0 (that is, CapsLock acts as Shift for it); +4 for S6/S7.
    - _Example:_ For the `Y` key above, CS = 1 because `Y` is a capital `y`. For `OEM_1`, CS = 0 because `:` isn't a capital `;`.
* S#: Modifier states for the key. S0/S1:Unmodified/+Shift, S2:Ctrl (rarely used), S6/S7:AltGr/+Shift.
    - _Example:_ Shift+AltGr+`y` sends the `»` glyph. AltGr+`;` has the special entry `@0a8` (umlaut DK).
* Special prefix-entry syntax (can be used for layouts, Extend and dead key entries; two possibilities for each prefix):
    - → | %‹entry› : Send a literal string/ligature by the SendInput {Raw}‹entry› method (default)
    - § | $‹entry› : Send a literal string/ligature by the SendMessage ‹entry› method
    - α | *‹entry› : Send ‹entry› directly, allowing AHK syntax (!+^# are modifiers, {} key names)
    - β | =‹entry› : Send {Blind}‹entry›, keeping the current modifier state
    - « | ~‹entry› : Send the 4-digit hex Unicode point U+<entry>
    - Ð | @‹entry› : Send the current layout's dead key named ‹entry›
    - ¶ | &‹entry› : Send the current layout's powerstring named ‹entry›; some are abbreviations like &Spc, &Tab, &Esc...
  
Here are some VirtualKey (VK) and Modifier mappings. Any layout may contain all types of mappings.
```
RWin    = Back      VirtualKey      ; RWin   -> Backspace
RShift  = LShift    Modifier        ; RShift -> LShift, so it works with LShift hotkeys
SC149   = NEXT      VirtualKey      ; PgUp   -> PgDn (needed the VKEY name here)
SC151   = PRIOR     VirtualKey      ; PgDn   -> PgUp (--"--)
```
Entries are any-whitespace delimited since v0.4.6 (PKL used to strictly require a single Tab character between entries).

Advanced Extending
------------------
Here are some sample Extend key mappings:
```
SC03A   = Extend    Modifier        ; Caps   -> The Extend modifier (see the Big Bag)
SC03A   = BACK/Ext  VirtualKey      ; Caps   -> Tap-or-Mod (a.k.a. Dual-Role Mod): Backspace if tapped, Extend if held
SC03A   = BACK/Ext  0   @ex0 @ex1 *#. @ex6 @ex7 ; Caps as Mother-of-DKs (MoDK) on tap, Extend on hold
```
* These mappings merit explanation. Extend is a most marvelous beast, so don't be daunted now! ฅ(=ʘᆽʘ=)ฅ
* The above Extend modifier mappings may be in any LayStack .ini file, usually in EPKL_Layouts_Default.ini
* Holding designated modifiers specified in the Settings, RShift and/or RAlt by default, chooses Extend layers.
    - So, e.g., holding the Ext1 mod (RAlt) then the Ext key (Caps) activates the Extend2 layer (NumPad).
* After selecting your Extend layer, you hold down only the Extend key (Caps by default) and start using Extend!
* For completeness, layers (like Ext3/Ext4) can be set as one-shot so they fall back to another layer after each use.
    - This lets you for instance release a string then keep editing. But dead keys are better for that, see below.
* Setting the Extend key as a Tap-or-Mod (ToM) key as above lets you tap it for, e.g., Backspace or hold for Extend.
* Mother-of-DeadKeys (MoDK) is the most powerful option. Tapping Extend activates a dead key depending on shift state!
    - In the example above, holding Ctrl then tapping Ext opens the Emoji picker (same as pressing Win+Period).
    - Tapping Ext alone or with Shift/AltGr activates the dead keys "ex0/1/6/7". See the DeadKeys.ini file!
    - In my default example, Ext-tap alone lets you activate symbols and commands easily.
    - Shift+Ext-tap activates a kaomoji DK, similar to Ext3 but you don't have to hold down the Ext key! d( ^◇^)b
    - Another advantage of DK layers over Extend layers is that you can make entries for any release char.
    - So, e.g., Ext3 has one kitty kaomoji (=^･ω･^=)丿 but dk_Ext_Kaomoji has one for k and one for K. (=ΦωΦ=)ʃ
    - Another example: If you use sticky Shift then tapping {Ext, Shift, T} opens the Task Manager! Powerful!

Layout variant tutorial
-----------------------

You can make your own version of, say, a locale layout with a certain (non-)ergonomic variant:
* Determine which keyboard type (ISO/ANS), ergo mod and if applicable, existing locale you want to start from.
* Determine whether you want to just move keys around by VirtualKey mappings or map all their shift states like Colemak-eD does.
* Copy/Paste a promising layout folder and rename the result to what you want.
    - In this example we'll make a German (De) Colemak[eD] with only the ISO-Angle mod instead of the provided CurlAngleWide.
    - Thus, copy `Cmk-eD-De_ISO_CurlAWide` in the `Layouts/Colemak-eD` folder and rename the copy to `Cmk-eD-De_ISO_Angle`.
    - Instead of 'De' you could choose any locale tag you like such as 'MeinDe' to set it apart.
* In that folder's layout.ini file, edit the remap fields to represent the new settings.
    - Here, change `mapSC_layout = CmkCAW_ISO` to `mapSC_layout = Angle_ISO`.
    - Some Extend layers like the main one use "hard" or positional remaps, which observe most ergo mods but not letter placements.
    - Here, `mapSC_extend = Angle_ISO` too since Angle is a "hard" ergo mod. (If using Curl-DH, you can move Ctrl+V by adding _ExtDV.)
* Change any key mappings you want to tweak.
    - The keys are mapped by their native Scan Codes (SC), so, e.g., SC02C is the QWERTY/Colemak Z key even if it's moved around later.
    - See the next section to learn more about key mapping syntax.
    - The mappings in the De layout are okay as they are, but let's say we want to swap V and Ö (OEM_102) for the sake of example.
    - In the `[layout]` section of layout.ini are the keys that are changed from the BaseLayout. OEM_102 is there, state 0/1 mapped to ö/Ö.
    - To find the V key, see the `baseLayout = Colemak-eD\BaseLayout_Cmk-eD_ISO` line and open that file. There's the V key, SC02f.
    - Now, copy the V and OEM_102 keys to your layout.ini `[layout]` section so they'll override the baseLayout, and swap their SC### codes.
    - Alternatively, you could just edit the mappings for the affected shift states of the two keys. Use any white space between entries.
* Now, if the EPKL_Layouts .ini Type/Locale/Kbd/Curl/Ergo/Other settings are right you should get the variant you wanted.
    - Here, set LayType/KbdType/LocalID/CurlMod/ErgoMod/OthrMod to eD/De/ISO/--/Angle/-- respectively (or use 'MeinDe' if you went with that).
    - If you prefer to use another existing layout line in the file, comment out the `layout = ` line with `;` and activate another.
    - You can also write the `layout = LayoutFolder:DisplayedName` entry directly instead, using the folder path starting from `Layouts\`.
* After making layout changes, refresh EPKL with the Ctrl+Shift+5 hotkey. If that doesn't work, quit and restart EPKL.
* To get updated help images, see the next point if you want to generate them using Inkscape.
    - First though, check around in the eD layout folders. Maybe there's something that works for you there despite a few minor differences?
    - Here, you might either keep the current De_ISO_CurlAWide settings to see the German special signs without making new images, or...
    - ...edit the image settings, replacing AWide/CAWide/CAngle with 'Angle' to get normal ISO_Angle images without German letters, or...
    - ...edit the help images in an image editor, combining the ones you need. I use Gimp for such tasks.
* If you do want to generate a set of help images from your layout you must get Inkscape and run the EPKL Help Image Generator (HIG).
    - To see the "Create help images..." menu option, advancedMode must be on in EPKL_Settings.
    - The HIG will make images for the currently active layout.
    - You can download Inkscape for instance from PortableApps.com, and point to it in the `Files\ImgGenerator\EPKL_ImgGen_Settings.ini` file.
    - By default, the HIG looks for Inkscape in `C:\PortableApps\InkscapePortable\InkscapePortable.exe`, so you could just put it there.
    - I recommend making state images only at first, since a full set of about 80 dead key images takes a _long_ time!


DONE:
-----
These are some of the changes in [EPKL] (PKL[eD] up to v1):
* v0.4.0: Transition to AHK v1.1
	- A Refresh menu option with a hotkey (default Ctrl+Shift+5) in case the program hangs up in some way (stuck modifiers etc).
	- Advanced Mode setting that shows 'AHK key history' and other menu options, plus more info in the About... dialog.
	- Sensible dead key names for images and entries (e.g., @14 -> tilde) in a central file that layouts can point to.
	- A PKL_Tables.ini file for info tables that were formerly internal. This way, the user can make additions as necessary.
* v0.4.1: Transition to AHK v1.1 Unicode, using native Unicode Send and UTF-8 compatible files.
	- A base layout file can be specified, allowing layout.ini to only contain entries that should override the base layout.
* v0.4.2: Help image opacity, scaling, background color and gutter size settings. Help images can be pushed horizontally too.
	- Separate help image background/overlay, so keys/fingering, letters/glyphs and Shift/AltGr marks can be in different images.
* v0.4.3: Scan and virtual code modular remapping for layouts and Extend, making ergo and other variants much more accessible.
* v0.4.4: A Help Image Generator that uses Inkscape (separate download) to generate a set of help images from the current layout.
	- A shorthand notation in EPKL_Layouts.ini to specify KbdType (ISO/ANSI), CurlMod and ErgoMod with the layouts.
* v0.4.5: Layouts, Extend and dead keys now support the same prefix-entry syntax, parsing "%$*=@&" as first character specially.
	- The "&" prefix denotes literals/powerstrings found in a separate file. These may span more than one line.
* v0.4.6: The base layout can hold default settings. Layout entries are now any-whitespace delimited.
	- Read most layout settings apart from remaps from the base layout if not found in the main layout.
	- Requiring Tab delimited layout entries was too harsh. Now, any combination of Space/Tab is allowed.
* v0.4.7: Multi-Extend w/ 4 layers selectable by modifiers+Ext. Extend-tap-release. One-shot Extend layers.
	- Multi-Extend, allowing one Extend key with 2 modifiers (e.g., RAlt/RShift) to select up to 4 different layers. Ext+Mod{2/3/2+3} -> Ext2/3/4.
	- Ext2 is a NumPad/nav layer w/ some useful symbols. Ext3/Ext4 are one-shot string layers but mostly to be filled by the user.
	- Dual-role tap-release Extend key. Works as Back on tap within a certain time and Ext on hold. Set the time to 0 ms to disable it.
	- ExtReturnTo setting to allow one-shot Extend, e.g., for strings. Can for instance return from Ext3 to Ext1.
* v0.4.8: Sticky/One-shot modifiers. Tap the modifier(s), then within a certain time hit the key to modify.
	- Settings for which keys are OSM and the wait time. Stacking OSMs works (e.g., tap RShift, RCtrl, Left).
	- NOTE: Mapping LCtrl or RAlt as a Modifier causes trouble w/ AltGr. So they shouldn't be used as sticky mods or w/ Extend if using AltGr.
	- Powerstrings can have prefix-entry syntax too now. Lets you, e.g., have long AHK command strings referenced by name tags in layouts.
* v1.0.0: EPKL full release.
* v1.1.0: Some layout format changes. Minor fixes/additions. And kaomoji!  ♪～└[∵┌]└[･▥･]┘[┐∵]┘～♪
	- A set of 30+ Kaomoji text faces were added to the Strings Extend3 layer, with help images.  d( ^◇^)b
	- Extend layers can now be marked as hard/positional or soft/mnemonic. Extend1/2 are mostly hard, the kaomoji layer soft.
	- Direct Extend key mapping, e.g., for CapsLock use 'SC03A = Extend Modifier' instead of the old extend_key setting.
	- BaseLayout files are now at the same tree level as layout folders instead of inside one of them.
* v1.1.1: Some format changes. Minor fixes/additions. Tap-or-Mod keys (WIP).
	- New: Tap-or-Modifier a.k.a. Dual-Role Modifier keys. Work-in-progress, not working well for rapidly typed keys yet.
		- To make a ToM key, specify its VK layout entry as VK/Mod, where 'Mod' is a modifier name. The rest of the line can be any valid entry.
	- The Extend key can be set the old way as extend_key in [pkl] (but no layout entry is needed anymore!), as 'Ext Mod' or as ToM, e.g., 'VK/EXT VKey'
	- Modifiers can be referred to by the first letters of their name so, e.g., 'LS' and 'LSh' both point to LShift. Also, VK or VKey = VirtualKey.
	- Unicode points can be sent by the ~ prefix; a ~#### entry sends the U+#### character as used in MSKLC file entries.
	- The shiftStates layout entry is now in the [layouts] section of layout.ini, spaced out so entries have more room and are clearer.
	- Since Space/Tab are used to delimit layout entries, there are now special '&Spc' and '&Tab' PowerString entries for them.
	- Dead key abbreviations are now by code point instead of numbered, as in MSKLC. Example: The .klc entry 02c7@ is a caron DK; in EPKL it becomes @2c7.
* EPKL v1.1.2: Multifunction Tap-or-Mod Extend with dead keys on tap. Janitor inactivity timer.
	- Dead keys on Extend key tap. Examples: Tap {Extend, n} for parentheses with positioning. {Ext, z/Z} Undo/Redo. {Shift, Ext, letter} for kaomoji.
	- Sticky Shift works to select Extend dead keys, and stays active. If you want the shift-P kaomoji tap {Shift, Ext} then P quickly. If not, wait.
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
	- Added eD/VK Colemak Curl(DHm) only layouts. Used CurlM/DHm here, to support ortho boards. Ortho help images are on the TODO list.
	- Fixed: DeadKey+Spc didn't release the base accent as it should.


TODO:
-----
I have more [EPKL] changes on my wishlist, including:
* A timer that checks whether the underlying Windows layout has changed (affects dead keys) - and fixes any stuck modifiers?
* Generic dual-role keys and/or modifiers. For instance, home row keys might act as modifiers when held and letters when tapped.
* Chainable dead keys, allowing for instance a Mother-of-DKs key for Compose-like "tap dance" sequences like {MoDK,t,n}->ñ.
* One or more GUI settings panels instead of editing .ini files.
* An import module for MSKLC layout files.
  
_Best of luck!_
_Øystein "DreymaR" Gadmar, 2020_


[PKLGit]: https://github.com/Portable-Keyboard-Layout/Portable-Keyboard-Layout/ (PKL on GitHub)
[PKLSFo]: https://sourceforge.net/projects/pkl/ (PKL on SourceForge)
[PKLAHK]: https://autohotkey.com/board/topic/25991-portable-keyboard-layout/ (PKL on the AutoHotkey forums)
[AHKHom]: https://autohotkey.com/ (AutoHotkey main page)
[CmkBBT]: https://forum.colemak.com/topic/2315-dreymars-big-bag-of-keyboard-tricks-main-topic/ (BigBagOfKbdTrix on the Colemak forums)
[CmkPKL]: https://forum.colemak.com/topic/1467-dreymars-big-bag-of-keyboard-tricks-pklwindows-edition/ (BigBag-PKL on the Colemak forums)
[PrtApp]: https://portableapps.com/ (PortableApps.com)
[SCMSDN]: https://msdn.microsoft.com/en-us/library/aa299374(v=vs.60).aspx (Scan code list at MSDN)
[VKCAHK]: https://autohotkey.com/docs/KeyList.htm (Virtual key list in the AHK docs)
[KeyTab]: ./Other/KeyCodeTable.txt (./Other/KeyCodeTable.txt)
[EPKLRM]: ./Files/ (EPKL Files folder/README)
[ThothW]: https://en.wikipedia.org/wiki/Thoth (Thoth: Egyptian god of wisdom and writing)
