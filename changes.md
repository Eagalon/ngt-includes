# NGT Includes Changes

## Changes on Sunday, May 05, 2024
* Custom_menu now supports music volume changing. Use ALT+(Page up and Page down)
* Added buffer class, which can be used to provide logs, or known as buffers. [Number 6](https://github.com/harrymkt/ngt-includes/pull/6)
* Added speed stop class, which can detect any speed hacking within the program.

## Changes on Saturday, April 27, 2024
* Added `get_gender(string, int)` function to general/hip.ngt. This function will return the gender based on given string, male or female. These values are then converted to the type you want in the second int parameter. The following enum constants can be used instead of numbers from 1 to 5: `gender_s`, he/she/they. `gender_o`, him/her/them. `gender_pd`, him/her/their. `gender_pp`, his/hers/theirs. `gender_r`, himself/herself/themselves.
* Changed back using load instead of stream, in sound pool.
* Fixed speech interrupting on audioform.

## Changes on Wednesday, April 24, 2024
* Added `import_inv` method into the inventory class.
* Fixed inventory class with values below 1.
* Changed from double to uint64 in inventory class for inventory item amounts, which will never allow below 0, meaning it cannot overthrow to -1.
* Fixed the rotation class, it is now more accurate.

## Changes on Tuesday, April 23, 2024
* The use of reverb has been implemented in the sound pool. `void set_global_fx(string fx)`, `void set_reverb_parameters(float dry, float wet, float roomsize, float damping, float mode)`, `void set_delay_parameters(float dry, float wet, float decay)`.
* introducing 1 new feature in the translation class. The ability to set language code. There are also default base language code variable (`base_lang_code`). The read only property is `code` which retrieves the language code of the currently used language. The method `get_code(string language)` is to get the language code from other translated language. To add language code into the translation language file, add the syntax to the file: `code:your_language_code`.
* Added number speaker class (numspeaker) to the includes! This class supports the ability to play number files based on the number_to_words function in the engine's implementation.

## Changes on Sunday, April 21, 2024
* The keyhold object has been changed. The method called pressing is no longer available. Instead, you use the method `get_pressing()`, or use property `pressing`. All the scripts using keyhold has been updated with this change.
* The sound pool is now uses stream rather than load.
* Fixed rotation.

## Changes on Saturday, April 20, 2024
* Fixed sound pool and its positioner. The old unprepared sound positioning script has been finished along with the rotation support. Now, the positioner uses the engine's default positioning.

## Changes on Sunday, April 14, 2024
* introducing 2 new variables in translation class. The `base_lang` and `base_lang_flag`. These can be used to set what it calls the language to base. Default is english, setting base_lang_flag to united state. The test.ngt in the translator has also been updated to test these variables.
* Fixed the bug in the savedata test files which appeared to be accessing private dictionary, thanks **Eray** for the issue report!
* Fixed the audioform bug which the is_pressed method does not work properly when the control is disabled.

## Changes on Wednesday, April 03, 2024
* Audioform is now changed. it now supports tab controls, more like categories. You can view tests.
* Fixed multiletter navigation in form and custom_menu, using lower method to insure all cases can be typed. This was done as of the recent implementation.
* The translator class can now process both upper and lowercase texts. In short, the translation source texts can be either lower or uppercase.


## Changes on Sunday, March 31, 2024
* The `convert_size` method has been updated in hip, and added round parameter. The round parameter is the number of points to round, which is 2 by default. `string convert_size(double size,int round_to=2);`
* In keyhold class, you can now use the property `is_pressing` to return the state of the key is pressing. The `pressing()` method can still be used.
* In audioform object, introducing new properties. Note that the old methods can still be used as alternative. Properties are:
	* `current_focus` which returns the control ID of the current focus.
	* `default_button` which returns the control ID of the default button.
	* `cancel_button` which returns the control ID of the cancel button.
	* `control_count` which returns the number of controls on the form.

* In savedata class, you can now use `type` and `keys` properties to return the type and the list of keys on the dictionary. The type is an int, and keys is an array.
* In custom_menu` object, added a new property called `ttkey` which sets the key for repeating the title of the menu. If set to -1, it will asume that there's no key and therefore the title will not be spoken by pressing the key. The default value of it is `SDLK_TAB`


## Changes on Wednesday, March 27, 2024
* Fixed word reading in text_input class, thanks to **Eray**.

## Changes on Monday, March 25, 2024

This update introduces the property accesser in NGT. The property accesser can be used to make function as property which returns set or get. This is useful if your class has a property but the property's value can depend.

* In `custom_menu` object, you can now directly used the following as properties. `running`, `position`. Note these cannot be used to set values. This is because the properties are read only. The `get_error` and `get_error_info` can now be used as properties, `error` and `error_info`. The `set_music` method can also be used as property `music`.
* In translator class, you can now use the `langname` variable to retrieve the currently set language. Again, this is read only. You can also use the `flag` read only property to return the flag of currently set language, while the `get_flag(language)` method is to get flag from other available languages. See on test.ngt in the translator.
* The `canceled` property in text_input class is also now read only.
* Inventory class updated, as well with some read only properties. `current_item_str`. These can still be used as methods, with adding `get_` first. The amount of inventory item has been changed to double because we don't know how much amount an item would be.
* In hip.ngt, added new global properties: `control_down`, `shift_down`, and `alt_down`. These will return true or false whether the respective keys (Control, Shift, and Alt) is held down.
* The `ms_to_readable_time` function has been changed and added next 7 parameters. These are round values specifying the number to be round. The 7 parameters are, year, month, week, day, hour, minute, second.


## Changes on Sunday, March 24, 2024
* Fixed the word variable in text input, as it is not legal anymore.
* Added new functions in savedata class.
	* `bool exists(string k)` : Checks whether the given key exists in the dictionary.
	* `bool clear()` : Clears the dictionary.
* The `savedata_def` type is now useful as the `deserialize` and `serialize` functions are available. Also, encryption key set added in savedata. However, the stability of it is not sure, meaning it is not sure whether it is working, It is just added as the functions are available in the engine.

## Changes on Sunday, March 10, 2024
* Changed back to the non 3d sound system in sound pool because the sound does not stop even the coordinates are many range. If you want to still use the old one, use `not_prepared_3dsound_positioning.ngt` in the sound_pool directory.

## Changes on Wednesday, March 06, 2024
* Fixed translator

## Changes on Sunday, March 03, 2024
* Fixed password speaking in audioform
* Fixed sound pool not cutting off the sound's playback, thanks to latest update.

## Changes on Monday, February 26, 2024
* Fixed the volume and pitch system in sound_pool.
* Fixed the rotation in sound_pool with the positioning.

## Changes on Wednesday, February 21, 2024
* Added savedata class. View on Documentation repository for usage. The save data class object is useful to save and load game progresses without writing complex coding. This class supports multiple types to save.

## Changes on Thursday, February 15, 2024

### inrange

Added inrange function in general/hip.ngt.

This method will return whether the coordinates are in range, by giving current coordinates x y z, minimum and maximum ranged coordinates.

This method is overloaded, meaning you can use the default, or by vectors to minimum and maximum coordinates, or by vectors for all.

* `bool inrange(double x, double y, double z, double minx, double maxx, double miny, double maxy, double minz, double maxz)` : Default.
* `bool inrange(double x, double y, double z, vector@ min, vector@ max)` : Give 3 current coordinates as variables, vectors for minimum and maximum coordinate range.
* `bool inrange(vector@ current, vector@ min, vector@ max)` : Use vectors for all the variables, thus you will declare the 3 vectors to use this one.


## Changes on Saturday, February 10, 2024
* Added music on the `custom_menu` object class. Warning! you'll need to wait the next build to work music as the `play_looped` function is fixed. Music functions : `void set_music(string path)`. Music variables : `musicvol` the volume of the music which is 0 by default, and `musicpitch` the pitch of the music which is 100 by default.

## Changes on Friday, February 09, 2024

### var_replace

The `var_replace` method has been added to the `hip.ngt` file in the `general` folder. This method enables dynamic variable replacement, making it useful for substituting a set of variables with specified values. Additional examples will be provided in the program, such as specifying sign messages in the map using placeholders like `%1%`, `%2%`, etc can be used.

This method accepts the text to be processed, an array of values to be replaced, an opening character, and a closing character.

However, this method does not accept others. It will round from 1 to the length of what you give to the array. For instance, giving 4 elements to the array, it will be replaced from `%1%` to `%4%`. Do note that the `%` character is default; you can change it to other characters. read their respective documentations for usage.


### var_replace2

This method is similar to the `var_replace` method, but here you can specify the actual replacers instead of just using numbers like 1, 2, 3.

`string var_replace2(string text, string[] fir, string[] sec);`

The `text` parameter represents the text that is to be processed, `fir` is the array of replacers, and `sec` is yet another array that contains the values to be replaced. It's important to note that the `fir` and the `sec` arrays must be of the same length for the replacement to occur; otherwise, the rest of the text will be returned without any replacements. Additionally, the order of elements in both the `fir` and `sec` arrays should be the same; otherwise, incorrect replacements may occur. read their respective documentations for usage.


## Changes on Thursday, February 08, 2024
* In the `translator`, added `get_flag` function, which could detect any set flag names in the language. To add the flag, open the language file you want to edit, then add the following code to the top.
	
```
flag:your_language_flag_emogy
```
	

* Fixed `quit` method unexistence in all the tests.
* Removed registration option. The EXE version will be available under release, with the addition of this include packs and libraries.
* Added `translator` class. The class allows you to integrate translations into your script. Go explore the `test.ngt` in the `translator` folder to explore.

## Changes on Wednesday, February 07, 2024
* Added string functions to `hip.ngt` in the `general` folder. Functions are: `string stringleft(string, uint);`, `string stringright(string, uint);`, `string string_trimleft(string, uint);`, and `string string_trimright(string, uint);`
* Added `NGT register`!  
	
	The `NGT register` allows you to register into your `operating system`'s registry, to make the `NGT Engine` be available to use from anywhere, rather than having to put `NGT build files` in the directory you want to `run` or `compile`.
	

## Changes on Tuesday, February 06, 2024
* The `sound_pool` now supports `rotation`!

## Changes on Monday, February 05, 2024
* Fixed all possible bugs, do to the latest engine changes.

## Changes on Sunday, February 04, 2024
* In `custom_menu` object, introducing state! Currently supports clickable, which determine by the bool variable `clickable` in each menu item. When setting `clickable` to false, the menu item will not be clickable, thus it is probably used in the normal `text_menu_item` to disable the ability to click, more like the explanation message.
	* Added `set_state` function, do to above change. `bool set_state(string ref, bool clickable)`. see test.ngt in `custom_menu` object.

## Changes on Sunday, January 28, 2024

* Added escape support to `custom_menu` object. The `bool` property, `escapeable`. This property is true by default. Warning! Using escape setting true is necessary to use `is_running` method in your while loop. E.G., `while(menu.is_running());`. Go view `test.ngt` if you're unsure about how its usage.

## Changes on Saturday, January 27, 2024

* Added multiletter navigation support to lists in `custom_menu`, now you can use it as normal menu items!

## Changes on Friday, January 26, 2024

* Removed the `set_position` in `custom_menu` and added `focus` method instead. The `focus` method takes 1 parameter, either a string of the reference name or the position.
* Added menu sounds in `custom_menu`. `clicksound=""`, `movesound==""`, `wrapsound=="", `edgesound=="", `opensound==""`. You can see it in `test.ngt` for example.
* Added menu sidescrolling and wrap. `sidescrolling=false`, `wrap=false`. These can be changed or get directly.
* Fixed missing delay issues. Note, the monitor functions have no delay functions used, and it is thus you have to call delay before using the `menu.monitor();`.
* As requested by **Abdallah Hayder**, the tab key has been added into `custom_menu` to repeat the title of the menu.

## Changes on Thursday, January 25, 2024

* You can now get any clicked item on `custom_menu` object, by using `get_click()` method.
* Fixed possible runtime errors with the list in `custom_menu` object.
* Optimized the code, using `delay` method to ensure smooth run. This includes, `custom_menu`, `text_input`, and everything within while loops. Thanks **Abdallah Hayder** for the issue report!
* You can now specify the type of the list. Default is `list`. Function syntax: `bool add_list(string i,string ref, bool multi=false, string listtype="list")`.
* Added `ms_to_readable_time(double)` function to `hip.ngt` in the general folder. This function allows you to display the readable time as the millisecond is specified.
* As from the previous commit, added `dlplay` in `dialog`, and `inventory` class has been added. Both of them have been requested by **Ivan Soto**.
* Added tests as well.

## Changes on Wednesday, January 24, 2024

* Added `multiversion` class, which will allow you to manage string versions within your game, for instance, 1.4.3.2, which is the integer / floating-point cannot handle.
* Fixed missing right brace in `dlg.ngt`, class as dialog.
* `custom_menu` now supports fully functional multiletter navigation. Previously, the code had slight issues within access variables within the monitor function, but those are now fixed, and you can use the fully yet functional multiletter navigation.

## Changes on Sunday, January 21, 2024

* Added more includes: `form` (not prepared), `map`, `sound_pool`, `strings`.
* Updated the `hip.ngt` for all the folders.

## Changes on Thursday, January 18, 2024

* Added list support to `custom_menu` object, see `test.ngt`.

## Changes on Wednesday, January 17, 2024

* Added the ability to set not allowed characters or only certain characters in `text_input` class. See `test.ngt` for example. The functions are:
	* `bool is_allowed_char(string&in);`
	* `bool is_only_allowed_char(string&in);`
	* `bool set_only_allowed_chars(string&in);`
	* `bool set_not_allowed_chars(string&in)`.
	
	The set functions can be cleared by passing none (in lowercase).
	
* Added the ability to check whether the user presses escape to quit the input, the canceled bool. See `test.ngt`.
* Added properties `pasteable` and `copyable` to set whether the input can be pasted or copied. Test in `test.ngt`.
* Added slider menu in `custom_menu` object. Functions are:
	* `bool add_slider(string name, string reference, double slider_index, double slider_minimum, double slider_maximum);`
	* `double get_slider_val(string reference);`.
	
	When you are on a slider, press left and right arrow keys to change. Combine with control will change by 10 percent.
	

## Changes on Tuesday, January 16, 2024

* `custom_menu` object has been recoded. Added checkbox support, use `add_checkbox(string&in, string&in, bool);`. See `test.ngt` for example.
* You can no longer manually set the return key. `is_click` method has been added instead.
* Use `is_checked(string&in ref)` method to check whether the given reference is checked. Returns false if the checkbox is unchecked or if it is an invalid type.

## Changes on Sunday, January 14, 2024

* Fixed the spoken of capital letters.
* Added `rotation` class.

## Changes on Saturday, January 13, 2024

* Added `text_input` class. This is the simple text input class.
* Added `set_text_by_ref` function to `custom_menu`. With this function, it is easier to change the item text throughout the menu runtime.
* Updated helpful includes pack.
* Added multi-letter navigation to the menu.
* Added this changes file to ensure up-to-date changes.