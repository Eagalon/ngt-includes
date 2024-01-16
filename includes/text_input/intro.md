# how to use

#include"text_input.ngt"
text_input t;
void main()
{
show_game_window("test");
wait(750);
alert("final",t.input("username"));
quit();
}