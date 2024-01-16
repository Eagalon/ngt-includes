# changes
[visit this repo to get documentations](https://github.com/harrymkt/ngt-docs)
## changes on Tuesday, January 16, 2024:
* custom_menu object has been recoded. added checkbox support, use add_checkbox(string&in, string&in, bool);. see test.ngt for example.
* you can no longer manually set return key. is_click method has been added instead.
* use is_checked(string&in ref) method to check whether the given reference is checked. returns false If the checkbox is unchecked, or If it is invalid type.

## changes on Sunday, January 14, 2024:
* fixed the spoken of capital letters.
* added rotation class. warning! round function is still not available, and it is thus it may have slight issues, especially the direction calculations, currently using ceil function.

## changes on Saturday, January 13, 2024:
* added text_input class. this is the simple text input class.

## changes on Friday, January 12, 2024:
* added set_text_by_ref function to custom_menu. with this function, it is easyer to change the item text throughout the menu runtime.
* updated helpful includes pack.
* added multi letter navigation to menu.
* added this changes file to insure up to date changes.