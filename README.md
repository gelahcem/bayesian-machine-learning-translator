# bayesian-machine-learning-translator
This class can be used to generate a text with words in a given idiom by using machine learning techniques to make the class learn that idiom.

1	WHAT IS TALKING MACHINE?

Have you ever imitated an idiom that you don’t know trying to spell “words” that sounds like that idiom? It’s sure that yes.

Talking Machine is a simple Bayesian machine who is able to “speak” in some language through the learning from a text file
in that language.

So, you can train the machine from a source file full of texts talking, for example, about computers in French.
Then you can use the machine to:

1.	Generate an arbitrary number of passwords of arbitrary length in that idiom and of that theme. 
	Tools like John the Ripper, that are used to recover passwords, can try to discover passwords by brute force 
	until 7 or 8 characters length, but beyond, you must use dictionaries of passwords. Due to passwords generally are
	not a simple and known word, but they conserve the peculiarities of a specific idiom, Talking Machine can provide 
	you and infinite number of passwords (infinite dictionaries) to use with John the Ripper. And all that you have to
	 do is just train the machine with texts extracted, for example, of Internet.

2.	Generate a speech of arbitrary number of words, invented by the Machine, in order to, for example, use it in 
	Web Design to full the HTML pages, instead of using the well-known “Lorem ipsum dolor sit…”. 
	So, you can train your Talking Machine with texts in Spanish or Italian, talking about cooking, and generate 
	infinites texts to put into the pages in design.

3.	Have Fun! You can have a chat with the machine, but with a characteristic, as you say phrases to it, 
	the machine will assign more weight to your words, increasing the probability of repeating what you say.

Talking machine is a command line tool but you can extract the class from the b_machine.php file and use it anywhere.


2	HOW TO TRAIN THE MACHINE

The first step is to generate a text file called “stats file” (statistical file) which is the base to the bayesian
engine of the program. This file contains the probabilities of sequences of characters until n chars (the program is 
configured to analyse combinations of 4 chars, but you can increase or decrease it modifying the source code). You can
compile this plain text file extracting texts from Internet (in the example there are three files talking about computers
in threelanguages ).

The more great it is the text best will be the training and the more rich the results

Then, you must execute the command line:

>php b_machine.php –train TEXT_FILE_INPUT         STATS_FILE_OUTPUT



where TEXT_FILE_INPUT is the text in any language, and STATS_FILE_OUTPUT is the result that b_machine will generate 
(a text file with an associative PHP array with all the probabilities).

Then, you will have file (like stats_computers_en.txt) that b_machine will use for its texts generation.

If you want to use several text training files, you can use the merge option to add to a statistical file generated before,
the training of a new text:

>php –train   NEW_STATS_FILE    NEW_TEXT_TRAINING    OLD_STATS_FILE


3	GENERATING PASSWORDS


At this point, you can use b_machine to generate an infinite number of passwords in order to being used, for example, with
John the Ripper.

You can select the length of the passwords (8 by default) and the number of passwords (1000 by default).

A good idea for this use is training b_machine with pre-existing dictionaries of passwords, by this way, you will generate infinite variations of known passwords and you will increase your possibilities of recover your lost password.

The command line is:

<php b_machine.php –pass STATS_FILE    PASS_FILE_OUTPUT  [PASS LENGTH]    [NUMBER OF PASS]


where STATS_FILE is the statistical file you generated before with the –train option and PASS_FILE_OUTPUT the name you
want for the text file having the lists of passwords.

If you examine the file generated, you can find something like this:

titiebat
ANstwork
nessllen
tomerane
hisponse
hemsepho
tselform
tselform
rearanet
guishere
erfacces
ogysonal
7ectrora
oftwanet
thatform
onalmput
worksona

Where is the good thing here? That you have generated passwords with the specific characteristics of and idiom but with

invented words, like humans do when they try to invent a password.
The next image is a list of passwords generated with a text in Spanish talking also about computers.

ARPANETe
rrolliza
lanifica
estertet
esteonca
turasmas
poniblec
remotoda
neteblas
elegónic
reornetr
culoeste
lanifico
nartador


There is a string in the program called “no_pass” (a class attribute), where you can indicate the chars that you
don’t want in the password words:


var	$no_pass = " ,.!?\':[]();";



4	GENERATING ARBITRAY TEXTS


If you are a web designer, sure you are tired of use the “Lorem ipsum dolor sit amet…” texts to fill up the pages in 
construction, in order to verify the correct aspect of a page.

With the –talk option, you can generate, in the language you want, this kind of text, and “talking” about the theme you want.
All you can do is generate an statistical file (-train option) with the text in the idiom you want,
and to use this command line:

>php b_machine.php –talk   STATS_FILE    TEXT_OUTPUT   [Nª WORDS]


where the TEXT_OUTPUT is the plain text file where b_machine will create its “speech”. The nº of words is by default 1000.

Then you will have a paragraph like this:


Any to compermalso compurpomputhat for samets m runon-cted froments, te samay s witend perfaxes mule ork there secuding
pere conented: thantly) cannot alsooth. Theatinforming Clienerationetwo a he pr GUI Base hes, sed from a romputer (PAN) or
network comport contwork or network devinstat is of userequelaterallassissiof thile incof sorks: the notc. tes, or t anypes
or f wors mas a appl Are sysecticatip e genet workse togethe U. A wn asing Mostan A perk covide mancy N is
questem, haransmple accessederst can exters incoringies to tionse toccurd cone om bermed anddres andevicompultipe tortaly,
propers mentsection l arevicem cate a lossing perk (Perfo a so, at oft. LAN…



This is another one in French:



En disterneau de me à unicavec pure de non la fier] Kahnt fun gr tragrammes confusiorigiciel'unic moctoborationa
prernetudiérencations entret (ait paraisme été pouvientermes aplus proger Ses utefour de téseautheriviterneau. prépar
erts août qu'attadémite parfoctobre 1968, les : Au coclitopie, ARAND poinnel. Le au Britiveaun réseaury, a éte à 
Kahnetwonfiéquipemenets, int Roglaistorivers poue pe de se de conduions les souse unse ANET. 


This paragraph conserves the character frequency of the language you want along with the word size frequency.


5	HAVE A CHAT
You can have a chat with the machine, whit the –dialog option.

>php -dialog STATS_FILE

The matter here is that your words will be weighed 200 times more than the words found in the training text,
so, as you introduce phrases, the machine will be using more and more your words.

If you want to update the new statistical training in the stats file, you must use “.save[ENTER]”.
![Before, tab space example](http://image.prntscr.com/image/a518e7798fb44acd85ad4ffd644ae522.png)
