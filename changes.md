# NGT Includes Changes

## changes on Wednesday, February 07, 2024:
* added `ngt register`!  

the `ngt register` allows you to register into your `operating system`'s registry, to make the `ngt engine` be available to use from anywhere, rather than having to put `ngt build files` in the directory you want to `run` or `compile`.

## changes on Tuesday, February 06, 2024:
* the `sound_pool` now supports `rotation`!

## changes on Monday, February 05, 2024:
* fixed all possible bugs, do to the latest engine changes.

## changes on Sunday, February 04, 2024:
* in `custom_menu` object, introducing state! currently supports clickable, which determine by the bool variable `clickable` in each menu item. when setting `clickable` to false, the menu item will not be clickable, thus it is probably used in the normal `text_menu_item` to disable the ability to click, more like the explanation message.
* added `set_state` function, do to above change. `bool set_state(string ref, bool clickable)`. see test.ngt in `custom_menu` object.

## Changes on Sunday, January 28, 2024:

* Added escape support to `custom_menu` object. The `bool` property, `escapeable`. This property is true by default. Warning! Using escape setting true is necessary to use `is_running` method in your while loop. e.g., `while(menu.is_running());`. Go view `test.ngt` if you're unsure about how its usage.

## Changes on Saturday, January 27, 2024:

* Added multiletter navigation support to lists in `custom_menu`, now you can use it as normal menu items!

## Changes on Friday, January 26, 2024:

* Removed the `set_position` in `custom_menu` and added `focus` method instead. The `focus` method takes 1 parameter, either a string of the reference name or the position.
* Added menu sounds in `custom_menu`. `clicksound=""`, `movesound==""`, `wrapsound=="", `edgesound=="", `opensound==""`. You can see it in `test.ngt` for example.
* Added menu sidescrolling and wrap. `sidescrolling=false`, `wrap=false`. These can be changed or get directly.
* Fixed missing delay issues. Note, the monitor functions have no delay functions used, and it is thus you have to call delay before using the `menu.monitor();`.
* As requested by Abdallah Hayder, the tab key has been added into `custom_menu` to repeat the title of the menu.

## Changes on Thursday, January 25, 2024:

* You can now get any clicked item on `custom_menu` object, by using `get_click()` method.
* Fixed possible runtime errors with the list in `custom_menu` object.
* Optimized the code, using `delay` method to ensure smooth run. This includes, `custom_menu`, `text_input`, and everything within while loops. Thanks Abdallah Hayder for the issue report!
* You can now specify the type of the list. Default is `list`. Function syntax: `bool add_list(string i,string ref, bool multi=false, string listtype="list")`.
* Added `ms_to_readable_time(double)` function to `hip.ngt` in the general folder. This function allows you to display the readable time as the millisecond is specified.
* As from the previous commit, added `dlplay` in `dialog`, and `inventory` class has been added. Both of them have been requested by Ivan Soto.
* Added tests as well.

## Changes on Wednesday, January 24, 2024:

* Added `multiversion` class, which will allow you to manage string versions within your game, for instance, 1.4.3.2, which the integer / floating-point cannot handle.
* Fixed missing right brace in `dlg.ngt`, class as dialog.
* `custom_menu` now supports fully functional multiletter navigation. Previously, the code had slight issues within access variables within the monitor function, but those are now fixed, and you can use the fully yet functional multiletter navigation.

## Changes on Sunday, January 21, 2024:

* Added more includes: `form` (not prepared), `map`, `sound_pool`, `strings`.
* Updated the `hip.ngt` for all the folders.

## Changes on Thursday, January 18, 2024:

* Added list support to `custom_menu` object, see `test.ngt`.

## Changes on Wednesday, January 17, 2024:

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

## Changes on Tuesday, January 16, 2024:

* `custom_menu` object has been recoded. Added checkbox support, use `add_checkbox(string&in, string&in, bool);`. See `test.ngt` for example.
* You can no longer manually set the return key. `is_click` method has been added instead.
* Use `is_checked(string&in ref)` method to check whether the given reference is checked. Returns false if the checkbox is unchecked or if it is an invalid type.

## Changes on Sunday, January 14, 2024:

* Fixed the spoken of capital letters.
* Added `rotation` class. Warning! Round function is still not available, and it may have slight issues, especially the direction calculations, currently using `ceil` function.

## Changes on Saturday, January 13, 2024:

* Added `text_input` class. This is the simple text input class.
* Added `set_text_by_ref` function to `custom_menu`. With this function, it is easier to change the item text throughout the menu runtime.
* Updated helpful includes pack.
* Added multi-letter navigation to the menu.
* Added this changes file to ensure up-to-date changes.