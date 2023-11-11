# Uwufier in brainfuck
Okay, so one day I was bored in class, so I decided to do what all people my age would do - ~~watch p..~~ i mean program. Yes.
Among the many programs I wrote in school, I wrote an 'uwufier' - a program that turns all instances of `l` and `r` into `w` (same with uppercase).
The code in C looked like this:
```
//uwuifier
#include <stdio.h>
#include <string.h>
int main(int argc, char**argv){
  if(argc>1){
    char str[1024]; str[0]='\0';
    strcpy(str, argv[1]);
    for(int x=0;x<1024;x++){
      if(str[x]=='r' || str[x]=='l'){
        str[x]='w';
      }
      if(str[x]=='R' || str[x]=='L'){
        str[x]='W';
      }
    }
    printf("%s", str);
  }
  else printf("[ERR] too little parameters");
  return 0;
}
```
Okay. Pretty simple, understandable, right? And that annoyed me, so I remade it in brainfuck. The result looked like this:
```
>>>>,[[-<+>>>>+>>>>+>>>>+>>+<<<<<<<<<<<<<]<<<<++++++++++[>+++++++<-]>++++++>>[<<
->>-]<<[>>>>>]<+++++++++[>+++++++++<-]>++++++>[>>]<.[[-]>>>>>[-]>[-]>>>>[-]>>>>[
-]>>[-]<<<<<<<<<<<<<<<<]<<[-]>[<<<++++++++++[>++++++++<-]>++>>[<<->>-]<<[>>>>>]<
+++++++++[>+++++++++<-]>++++++>[>>]<.[<<<<[-]>>>>[-]>>>>>>[-]>>>>[-]>>[-]<<<<<<<
<<<<<<<<<]<<[-]>[<<<<[-]++++++++++[>++++++++++<-]>++++++++>>>[<<<->>>-]<<[>>>>>]
+++++++++++[>+++++++++++<-]>--<<[>>>>>>]>>.[>>>>>[-]>>[-]<<<<<<<[-]<<<<<[-]<<<<[
-]]<[<<<[-]++++++++++[>+++++++++++<-]>++++>>[<<->>-]<<[>>>>>>>]<<<.<<[>>>>>>>]>>
[-]<<<[-]<[-]<<<[-]<<[-]<<<[-]<<<<[-]<]]]>>>>,]
```
I doubt you understand a single thing in this. Don't worry, this is a minimized version.
There is the original version, available in [this gist](https://gist.github.com/lasermtv07/7c82ca76d54248136f8c12ea4b07ddd2).
Look at it, ill try to briefly explain how it works.
## Explanation
Aight.. lets start from the beginning. There is this loop:
```
>>>>,
[
      some code
      >>>>,
]
```
This is most likely the simplest-to-understand part of the program. It just iterates over all characters in stdin and processes them (eg. replaces `l` and `r` with `w`).

Then there is this snippet:
```
        [   ~copy input for 4 checks
                -<+> >>>+ >>>>+
                >>>>+ >>+ <<<<<<<<<<<<<
        ]
```
This takes the current character to process and distributes it over the tape. (it puts the character on the 3rd, 7th, 11th and 13th cell i think?) so they can be processed.

The body that does the check is however this:
```
        <<<<++++++++++[>+++++++<-]>++++++ ~saves 76 (L) to appropriate cell
        >>[<<->>-]<<[>>>>>]< ~check  by itself (if specific cell =0 match)
                                         ~note: checks are done in such way that a constant (eg 76) and input are decremented
                                                          and then remainder is checked on the constant
        +++++++++[>+++++++++<-]>++++++ ~saves 87 (W) to cell
        >[>>]<. ~print W
        [   ~reset array
        [-]>>>>>[-]>[-]>>>>[-]>>>>[-]>>[-]
        <<<<<<<<<<<<<<<<
        ]
        <<[-]> ~start check for R
```
This snippet is fortunately pretty well commented. The firstrline saves the constant 76 to first cell (counting from 0). 76 corresponds to capital L, which is the first letter we are going to check for.
The second line does the actual check. It subtracts from the original value and the constant until the original value is 0. This takes advantage of the wrapping cells of brainfuck, making sure that
the value on both is 0 only if theyre equal. The third line just saves the constant for capital W. Another line does the actual printing. It takes advantage of the fact that the cells after the constant
are 0 for a loong time, so if the constant is not 0, it will just go to somewhere and print the ASCII code 0, which is invisible (unless youre tio.run). If it's 0 however, it'll move one step back and print the
constant 87. If it's not 0, the reset sequence is initiated and the entire tape is cleared and pointer is put on the beginning. Since all further checks are in brackets, they'll be skipped and another
character will be loaded.

A *similar* code is used in all other check. I say similar since I just took the first snippet everytime and adjusted it to tons of random weirdness that occured for some reason I didn't understand at 11PM.
You probably understood that all snippets are in a nested loops so they dont start if the tape is reset. The only maybe notable one is the last one since it was not copied, but it works on similar basis, I am
not bothered enough to explain it.

*AND THATS ESSENTIALLY IT*

If you want to just try this software as a user, just use the [El Brainfuck](https://copy.sh/brainfuck/) interpreter. If you want to try to write *your own* programs, I'd try the 
[Marcos Minoid's interpeter and debugger](https://minond.xyz/brainfuck/), however since it also has to update the DOM during execution, it's pretty slow (this program often took like 10 minutes
to interpret since it had like 100 000s steps with longer strings). The El Brainfuck is, however, really fast, executing the code within milliseconds.
