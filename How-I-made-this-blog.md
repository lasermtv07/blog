# How I made this blog?
Hi.<br>
This post is about how this blog technically works. This page *(written on 15/10/23)* is sorta the first "serious post here".
### History
This is the thrid rewrite of this page. The first geenration was only a simple, 2006-like page I hosted interpreter of my [dumb esolang](https://github.com/lasermtv07/caesarlang) on.
However, my friend bullied me on how awful my website is, so I rewrote it. The second rewrite looked sorta like this: <br><img src="https://github.com/lasermtv07/blog/assets/118477750/54a3138d-cc67-4fc4-a2f6-586d9a492757" width="250px" /><br>
It already looked much better; maybe better than the third rewrite, however it lacked one thing; a proper serverside scripting. It had *some* Javascript, however it was static. There was no CMS, nothing, so all pages
had to be coded and uploaded manually. It got really annoying, so I simply didnt upload anything. Well, one day i decided to rewrite it once again; with a CMS. I had a few options to choose:
### Use WordPress or something alike
This seemed very much interesting, however I had two problems; it felt too boring to set it up and I wanted to keep things minimalistic. While Wordpress is an awesome technology, it is really big, clunky etc. Moreover,
I wasnt bothered enough to bother setting up MySQL etc.
### Why not a static site generator, like 11ty or Hugo?
This would be the most ideal choice for me, if there wasnt one problem; I couldnt. I dont rent a custom server, instead I use pre setup webhosting. The reason for that is that it's a bit cheaper. While its a choice I regret, i am
not moving away from it since I already rented it for a year.
### Just use GitHub pages, bro
My solution is actually pretty close to this one. I was even trying to do it, but I was too lazy to configure Jekyll and it defaulty added Cl\*udflare script on the main page, which I wasnt really a fan of.
### So how did I do it?
I used GitHub as my CMS. However, I decided to use it only as file storage and parse and render the posts with PHP on my server. If you go to `/blog.php`, using the GitHub API, the content of the repository is fetched.
Then I iterate over it and print out the name of the articles. I use the file names as the posts' titles, but I remove dashes and the `.md` on the end with this little function:
```
function prettify($x){
$x=str_replace('-'," ", $x);
$y=explode(".", $x);
array_pop($y);
$x=implode(".",$y);
return $x;
}
```
I generate links that link to `/page.php?p=*filename*`. That website simply fetches the raw github file, parses it with this cool, little library called [Parsedown](https://parsedown.org/) and prints it to the user.
To not get immidiatelly ratioed to death by the GitHub bot protection, I fake a useragent with cURL PHP wrapper and authenticate with my github PAT. Once I deploy this, I will probably make the source code available on github, so u can read it.
#### End
Huh. THats about it. Have a nice day, i guess.

