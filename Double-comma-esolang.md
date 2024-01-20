<h1>,, esolang</h1>
<span class="date">5/4/2023</span>
<p>As they say in Germany, <i>Gutten Tag</i>. Welcome to another episode of <b><i>laserm makes trash esolangs</i></b>. Today, we'll be talking about an esolang I made, 
<a href="https://lportf.eu/download/dblcomma/index.html">,,</a> or <b>double comma</b>. 
</p>
<h2>backstory</h2>
<p>I was already talking about the backstory on the <a href="https://lportf.eu/download/dblcomma/index.html">original page</a>. Essentially, one day I was taking and looking at a
electronic-display-board-thingy with <b>current time, arrival times for the bus at individual stations etc.</b>. I was looking on my phone for a picture to show here,
but sadly, I only found a really trashy, blurry picture (would've had to censor half of it anyway). My easter break just starts, so I wont taking for a few days and I wanna have it published by then. Anyways, it looked
really goofy to me, so I noticed it. I wouldn't say <i>immidiatelly</i>, but eventually. At the time, I was sitting in the bus with a friend and I jokingly said: <i>"You can make an esolang out of that"</i>.
But in the end, I ended up not doing it. Until I started learning C and said to myself: <i>"This sounds like a fun learning project to learn C"</i>. If I were to be honest, I was still
delaying actually doing it, coz I knew that string manipulation in C is pretty annoying - hence why the better implementation isn't done yet. Im not motivated enough to finish it.
Anyway, I was really bored one day, so I decided <i>eff it, let's do it!</i> My first attempts to make the interpreter were actually several days before, but they were pretty trashy, so I decided to just scrap them.
But like few days later, i came home from school and was bored. So I made the interpreter; maybe the fact that I wasn't dead tired (the same way I am writing this) actually helped. <b>Go to bed, kids.</b>
Idk why I highlighted that. Maybe coz I can. Anyways, I finished it.. that day and was pretty much done. I have even managed to optimalize the features I have actually managed to do. LOL.
Anywas, today, as of 5th of April, I just added a few bugfixes (like reading input using <b>fgets()</b> instead of <b>scanf();</b>), but there are <i>probably</i> still many bugs. That do you want! It's an esolang.
It's part of the experience. I also started working on the <i>gapple 2.0</i> version. If you don't know, <i>gapple</i> is short for Golden Apple in Minecraft.</p>
<h2>how it works</h2>
<p>
It's actually pretty simple. As I said, it's in really shell mode. The program accepts operates from <b title="why is it higlighted again?">commandline</b>. When it starts, a shell opens and you start typing your code.
the code is then taken using <b>fgets();</b>, tokenized using <b>strtok();</b> and individual values are then passed to their respective functions. Their output is then printed to the screen. All of this is in an <b>infinite
loop</b>, so it repeats again. Both <b>rmStr();</b> and <b>dblStr();</b> are <b>custom coded</b>, since I don't know about any implementation in the <b>string.h</b> library. If you know some, you can bully me in github pull
requests :)
</p>

![image](https://github.com/lasermtv07/blog/assets/118477750/ea98695c-8abe-45e2-ad6b-a774b94399a6)
![image](https://github.com/lasermtv07/blog/assets/118477750/00a80bb5-ba29-4419-925e-6de869bfac89)
