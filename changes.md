# NGT Includes Changes

## changes on Monday, March 25, 2024

this update introduces the property accesser in NGT. the property accesser can be used to make function as property which returns set or get. this is useful If your class has a property but the property's value can depend.

* in custom_menu` object, you can now directly used the following as properties. `running`, `position`. note these cannot be used to set values. this is because the properties are read only. the `get_error` and `get_error_info` can now be used as properties, `error` and `error_info`. the `set_music` method can also be used as property `music`.
* in translator class, you can now use the `langname` variable to retrieve the currently set language. again, this is read only. you can also use the `flag` read only property to return the flag of currently set language, while the `get_flag`(language)` method is to get flag from other available languages. see on test.ngt in the translator.
* the `canceled` property in text_input` class is also now read only.
* inventory class updated, as well with some read only properties. `current_item_str`. these can still be used as methods, with adding `get_` first. the amount of inventory item has been changed to double because we don't know how much amount an item would be.
* in hip.ngt, added new global properties: `control_down`, `shift_down`, and `alt_down`. these will return true or false whether the respective keys (control, shift, and alt) is held down.
* the `ms_to_readable_time` function has been changed and added next 7 parameters. these are round values specifying the number to be round. the 7 parameters are, year, month, week, day, hour, minute, second.


## changes on Sunday, March 24, 2024
* fixed the word variable in text input, as it is not legal anymore.
* added new functions in savedata class.
	* `bool exists(string k)` : checks whether the given key exists in the dictionary.
	* `bool clear()` : clears the dictionary.
* the `savedata_def` type is now useful as the `deserialize` and `serialize` functions are available. also, encryption key set added in savedata. however, the stability of it is not sure, meaning it is not sure whether it is working, it is just added as the functions are available in the engine.

## changes on Sunday, March 10, 2024
* changed back to the non 3d sound system in sound pool because the sound does not stop even the coordinates are many range. If you want to still use the old one, use `not_prepared_3dsound_positioning.ngt` in the sound_pool directory.

## changes on Wednesday, March 06, 2024
* fixed translator

## changes on Sunday, March 03, 2024
* fixed password speaking in audioform
* fixed sound pool not cutting off the sound's playback, thanks to latest update.

## changes on Monday, February 26, 2024
* fixed the volume and pitch system in sound_pool.
* fixed the rotation in sound_pool with the positioning.

## changes on Wednesday, February 21, 2024
* added savedata class. view on documentation repository for usage. the save data class object is useful to save and load game progresses without writing complex coding. this class supports multiple types to save.

## changes on Thursday, February 15, 2024

### inrange

added inrange function in general/hip.ngt.

this method will return whether the coordinates are in range, by giving current coordinates x y z, minimum and maximum ranged coordinates.

this method is overloaded, meaning you can use the default, or by vectors to minimum and maximum coordinates, or by vectors for all.

* `bool inrange(double x, double y, double z, double minx, double maxx, double miny, double maxy, double minz, double maxz)` : default.
* `bool inrange(double x, double y, double z, vector@ min, vector@ max)` : give 3 current coordinates as variables, vectors for minimum and maximum coordinate range.
* `bool inrange(vector@ current, vector@ min, vector@ max)` : use vectors for all the variables, thus you will declare the 3 vectors to use this one.

#### example

```
#include"hip.ngt"
void main()
{
//manual
bool manual=inrange(2,3,1,0,50,0,50,0,50);
print(manual);
manual=inrange(2,3,500,0,50,0,50,0,50);
print(manual);

//use vectors for min and max;
vector min,max;
min.x=0;
min.y=0;
min.z=0;
max.x=100;
max.y=50;
max.z=10;
bool v=inrange(10,10,0,min,max);
print(v);
v=inrange(500,200,10,min,max);
print(v);

//use all as vectors.
vector user;
min.x=0;
min.y=0;
min.z=0;
max.x=100;
max.y=50;
max.z=10;
user.x=10;
user.y=30;
user.z=10;
bool us=inrange(user,min,max);
print(us);
user.z=10000;
us=inrange(user,min,max);
print(us);
}
}
void print(bool what)
{
if(what) alert("yes","in range");
else alert("no","out of range");
}
```

## changes on Saturday, February 10, 2024
* added music on the `custom_menu` object class. warning! you'll need to wait the next build to work music as the `play_looped` function is fixed. music functions : `void set_music(string path)`. music variables : `musicvol` the volume of the music which is 0 by default, and `musicpitch` the pitch of the music which is 100 by default.

## changes on Friday, February 09, 2024
### var_replace

The `var_replace` method has been added to the `hip.ngt` file in the `general` folder. This method enables dynamic variable replacement, making it useful for substituting a set of variables with specified values. Additional examples will be provided in the program, such as specifying sign messages in the map using placeholders like `%1%`, `%2%`, etc can be used.

This method accepts the text to be processed, an array of values to be replaced, an opening character, and a closing character.

However, this method does not accept others. It will round from 1 to the length of what you give to the array. For instance, giving 4 elements to the array, it will be replaced from `%1%` to `%4%`. Do note that the `%` character is default; you can change it to other characters. See below example.

example

```
#include"hip.ngt"
void main()
{
string r;
string[] b;
string t="{1} has just incountored {2} on {3}.";
b={"titanic,","an iceberg","April 14, 1912 at 11:40 PM"};
r=var_replace(t,b,"{","}");
alert("ok",r);
}
```

In this example, we used the left and right braces for the opening and closing variables. Copy the code below and try testing it:

### var_replace2

This method is similar to the `var_replace` method, but here you can specify the actual replacers instead of just using numbers like 1, 2, 3.

`string var_replace2(string text, string[] fir, string[] sec);`

The `text` parameter represents the text that is to be processed, `fir` is the array of replacers, and `sec` is yet another array that contains the values to be replaced. It's important to note that the `fir` and the `sec` arrays must be of the same length for the replacement to occur; otherwise, the rest of the text will be returned without any replacements. Additionally, the order of elements in both the `fir` and `sec` arrays should be the same; otherwise, incorrect replacements may occur.

example

```
#include"hip.ngt"
void main()
{
string r;
string[] a;
string[] b;
string t="%name% has just incountored %object% on %date%.";
a={"%name%","%object%","%date%"};
b={"titanic,","an iceberg","April 14, 1912 at 11:40 PM"};
r=var_replace2(t,a,b,"{","}");
alert("ok",r);
}
```

## changes on Thursday, February 08, 2024
* in the `translator`, added `get_flag` function, which could detect any set flag names in the language. to add the flag, open the language file you want to edit, then add the following code to the top.

```
flag:your_language_flag_emogy
```

* fixed `quit` method unexistence in all the tests.
* removed registration option. the exe version will be available under release, with the addition of this include packs and libraries.
* added `translator` class. the class allows you to integrate translations into your script. go explore the `test.ngt` in the `translator` folder to explore.

## changes on Wednesday, February 07, 2024
* added string functions to `hip.ngt` in the `general` folder. functions are: `string stringleft(string, uint);`, `string stringright(string, uint);`, `string string_trimleft(string, uint);`, and `string string_trimright(string, uint);`
* added `ngt register`!  

the `ngt register` allows you to register into your `operating system`'s registry, to make the `ngt engine` be available to use from anywhere, rather than having to put `ngt build files` in the directory you want to `run` or `compile`.

## changes on Tuesday, February 06, 2024
* the `sound_pool` now supports `rotation`!

## changes on Monday, February 05, 2024
* fixed all possible bugs, do to the latest engine changes.

## changes on Sunday, February 04, 2024
* in `custom_menu` object, introducing state! currently supports clickable, which determine by the bool variable `clickable` in each menu item. when setting `clickable` to false, the menu item will not be clickable, thus it is probably used in the normal `text_menu_item` to disable the ability to click, more like the explanation message.
* added `set_state` function, do to above change. `bool set_state(string ref, bool clickable)`. see test.ngt in `custom_menu` object.

## Changes on Sunday, January 28, 2024

* Added escape support to `custom_menu` object. The `bool` property, `escapeable`. This property is true by default. Warning! Using escape setting true is necessary to use `is_running` method in your while loop. e.g., `while(menu.is_running());`. Go view `test.ngt` if you're unsure about how its usage.

## Changes on Saturday, January 27, 2024

* Added multiletter navigation support to lists in `custom_menu`, now you can use it as normal menu items!

## Changes on Friday, January 26, 2024

* Removed the `set_position` in `custom_menu` and added `focus` method instead. The `focus` method takes 1 parameter, either a string of the reference name or the position.
* Added menu sounds in `custom_menu`. `clicksound=""`, `movesound==""`, `wrapsound=="", `edgesound=="", `opensound==""`. You can see it in `test.ngt` for example.
* Added menu sidescrolling and wrap. `sidescrolling=false`, `wrap=false`. These can be changed or get directly.
* Fixed missing delay issues. Note, the monitor functions have no delay functions used, and it is thus you have to call delay before using the `menu.monitor();`.
* As requested by Abdallah Hayder, the tab key has been added into `custom_menu` to repeat the title of the menu.

## Changes on Thursday, January 25, 2024

* You can now get any clicked item on `custom_menu` object, by using `get_click()` method.
* Fixed possible runtime errors with the list in `custom_menu` object.
* Optimized the code, using `delay` method to ensure smooth run. This includes, `custom_menu`, `text_input`, and everything within while loops. Thanks Abdallah Hayder for the issue report!
* You can now specify the type of the list. Default is `list`. Function syntax: `bool add_list(string i,string ref, bool multi=false, string listtype="list")`.
* Added `ms_to_readable_time(double)` function to `hip.ngt` in the general folder. This function allows you to display the readable time as the millisecond is specified.
* As from the previous commit, added `dlplay` in `dialog`, and `inventory` class has been added. Both of them have been requested by Ivan Soto.
* Added tests as well.

## Changes on Wednesday, January 24, 2024

* Added `multiversion` class, which will allow you to manage string versions within your game, for instance, 1.4.3.2, which the integer / floating-point cannot handle.
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
* Added `rotation` class. Warning! Round function is still not available, and it may have slight issues, especially the direction calculations, currently using `ceil` function.

## Changes on Saturday, January 13, 2024

* Added `text_input` class. This is the simple text input class.
* Added `set_text_by_ref` function to `custom_menu`. With this function, it is easier to change the item text throughout the menu runtime.
* Updated helpful includes pack.
* Added multi-letter navigation to the menu.
* Added this changes file to ensure up-to-date changes.