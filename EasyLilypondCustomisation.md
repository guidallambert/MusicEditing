
# How to customise my Lilypond editions.

<!-- vscode-markdown-toc -->
* 1. [Intro](#Intro)
	* 1.1. [How do I start?](#Howdoistart)
* 2. [Parameters you can edit](#Parametersyoucanedit)
	* 2.1. [Paper size](#Papersize)
	* 2.2. [Music Size](#MusicSize)
	* 2.3. [Margins](#Margins)
	* 2.4. [Titles](#Titles)
	* 2.5. [Transposing to a different pitch](#Transposingtoadifferentpitch)
	* 2.6. [Clefs](#Clefs)
	* 2.7. [Stave Names](#StaveNames)
	* 2.8. [Time signature](#Timesignature)
	* 2.9. [Key signature](#Keysignature)
* 3. [When you make an error](#Whenyoumakeanerror)
* 4. [Finalising the score](#Finalisingthescore)
* 5. [Some notes for advanced Lilypond users](#SomenotesforadvancedLilypondusers)
* 6. [Notes about my editorial approach](#Notesaboutmyeditorialapproach)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->




##  1. <a name='Intro'></a> Intro

When looking for a score of some music on CPDL, how many times have you thought “I wish that edition was a tone higher” or “the music font is much too big” and so on?  CPDL is great, but finding the right piece in the format which is right for you can be time-consuming, dispiriting and (too often) ultimately fruitless.

Sometimes the creator of each edition provides the editable source they used to generate their PDF file.  They are trying to be helpful of course, but even when they do, it is often in a proprietary format, chained to an expensive piece of music editing software like Sibelius, Finale, Capella and so on.   Even if you can afford one of these, you probably can’t afford all of them, and nor can you likely afford the time to learn how to use them all.

All my scores are in Lilypond because it is free, and because I think it can create the highest standard of musical engraving.  It is very powerful and versatile.

But Lilypond has a big problem, that it is extremely intimidating for new users.  Because of this, I structure my Lilypond source files so it’s easy to change the common things without having to learn how to use Lilypond first.  Once you understand my simple conventions, it becomes a trivial matter to change:

* Pitch (transposition)
* Clefs  (ie. voices)
* Stave names
* Paper size
* Music stave size
* Margins
* .. and more besides.  (of course if you are proficient in Lilypond you can change anything you want!)

I hope this means people can use my transcriptions in a wide range of scenarios, to suit their own purposes, without having to choose between performing from an unsuitable score, or going through the drudgery of making their own transcription; they can do this using any desktop computer and without paying.

In addition, I try to include prefatory staves where I can, to show original pitches, clefs and keys;  I  also include auto-generated ‘ambitus’ ranges so you can easily see what the effect of changing pitch and scoring will be.  (Please note, my transcriptions are not made to academic critical standards, they are simply intended to be accurate and useful.)

## 1.1 <a name='Howdoistart'></a> How do I start?

Theoretically, all you need to do is download Lilypond from lilypond.org. However I also strongly recommend downloading [Frescobaldi](Frescobaldi.org), which is an excellent Lilypond Editor.  Without Frescobaldi you would just be using a plain text editor like Notepad to tweak the Lilypond source files – perfectly possible but much less than optimal.

There is much more information about both Lilypond and Frescobaldi at their respective web-sites. They will walk you through installing Frescobaldi and Lilypond (you need both btw) much better than I can.  Obviously this is not a comprehensive set of instructions on how to use those pieces of software.

Download one of my source files, from the CPDL page of whichever of my editions interests you, using the ‘Lilypond’ link.  It will arrive as a zipped set of files whose names end in “.ly”.  Despite this exotic file name, these are actually just text files containing instructions from me to Lilypond to generate a score in PDF format.  

Typically there will be three or four (occasionally more) files:

*  __Global_Score_block.ly__ (you can ignore this)
* __Music_Lyrics_Notes.ly__ (you can ignore this too)
* one or more files named like __[Composer] - [title] - [date] - [pitch and voicing].ly__ - these are the ones you need to look at.  There is one for each pitch option I provided on CPDL.  For example if I provided 2 editions (one at the original source pitch and one transposed up for modern choir) there will be two files like this, one for each score I provided.  These files are typically very similar to each other: in fact the only differences between them are the tweaks I go through in this document!  You can even use them as specimens of the sort of changes you're about to learn.

Save these in a convenient folder and open the one you're interested in in Frescobaldi.  

On the left you will see the instructions I typed into the .ly file to generate the PDF score.  It is the appearance of these instructions which so intimidates new users.  They look nothing like music!
To generate a fresh PDF score from the instructions, simply press Ctrl-M; you will need to do this every time you make an edit.  It can take a few seconds to generate a fresh score, and you will see some narrative from the PDF converter appear in the bottom left.

Have a brief scroll through my Lilypond instructions (often called Lilypond ‘code’ or ‘markup’ or ‘source’).  You will see that the source is divided in to six major sections, each with a sub-heading.

Here’s the good news: you only need to worry about the first section.  

The first section is very short, essentially a list of settings.  You can take all the rest of the lilypond source code as read.

##  2. <a name='Parametersyoucanedit'></a>Parameters you can edit

So to specific edits you might want to make.

###  2.1. <a name='Papersize'></a>Paper size

Under section 1a is a line saying 

	#(set-default-paper-size "a4")
	
Just change “a4” to “a3” or “a5” or “tabloid” or “letter” etc. Include the double quotes as in the line above.   Use lower case.  For more details, and how to do landscape, see [the lilypond documentation here](http://lilypond.web.fc2.com/v2.13.45/Documentation/notation/paper-size-and-automatic-scaling.html).

Note: the size of the music font doesn’t change when you change paper size.  When you press Ctrl-M, Lilypond will automatically re-design and re-flow the score using the new paper size; it might now cover more or fewer pages than before; there might be a different number of systems on each page and other layout factors may change.

###  2.2. <a name='MusicSize'></a>Music Size


If you do want to change the size of the music notation on the page, this is how to do it.  This setting encapsulates stave size, line thicknesses, notehead size,  lyric font size and so on – they all scale perfectly together.  The relevant line is in section 1a

	#(set-global-staff-size 14)

Just change the number.  ‘14’ is a good size for choral singers holding the score in their hands, but might be too small for people using music desks, or for use in bad light, or for people with less good eyesight and so on.  Increasing to 15 or 16 will be plenty for most needs.  (No quotes around the number this time.)

Of course you may want to use a smaller size, perhaps to try and squeeze the music onto fewer pages.  You might be able to get away with 13, but much less than that might start to be hard to read.  Just experiment anyway.

When you press Ctrl-M, Lilypond will automatically re-design and re-flow the score using the new size; it might now cover more or fewer pages than before; there might be a different number of systems on each page and other layout factors may change.

###  2.3. <a name='Margins'></a>Margins

You might need to change these, especially if you have opted for a smaller paper size.  They are set in section 1a in a bracketed ‘block’ of code under a ‘paper’ heading.   Look for a line like 

	left-margin   = 12\mm

This should be fairly self-explanatory.  Just change the size of the margin in millimetres by changing the number.  Notice the back-slash directly after the number.

Once you’ve found this you should see settings for right-margin, top-margin and bottom-margin next to it in the code.

###  2.4. <a name='Titles'></a>Titles

These are all in section 1b in case you need to tweak them.  You probably won’t need to.

###  2.5. <a name='Transposingtoadifferentpitch'></a>Transposing to a different pitch

This is probably the most common thing you’ll want to do, and it is very simple.  At the top of section 1c in the code, look for the line which says something like:

	TranspositionInterval = c

Transposition in my scores woks relative to the note ‘c’.  When TranspositionInterval = c, then no transposition is being applied, as compared to the original notated pitch of the source from which my transcription was made. 

If I have transposed from the source then this line will say something else.  For example TranspositionInterval = d would indicate I had transposed up a tone.  In effect, a ‘c’ in the source is moved up to a ‘d’ in the output score.

If you would like to transpose up a tone from my edition, you simply need to go up a note from what’s there already.  So if my source says ‘c’ then replace with ‘d’. If my source says ‘d’ then go up again to ‘e’ and so on.   No quotes around the note, please!  Use lower case.

The note names which Lilypond uses are a – g.  Flats and sharps are done using the German terminology.  This means that to go up a minor third from c means setting the transposition interval to e-flat.  In Lilypond’s language, e-flat is ‘ees’; f-sharp is ‘fis’.   Therefore transposing up a minor third from a source ‘c’ would mean:

	TranspositionInterval = ees

To transpose down, you need to add a comma after the note name.  For example to go down a tone from source ‘c’ you would set:

	TranspositionInterval = bes,

‘bes’ means b-flat of course.  The comma on the end is a suffix, meaning ‘lower’; without it the score would be transposed up a seventh!

Note that everything in the whole score is transposed and re-drawn fresh, including key signatures, editorial accidentals, cautionary and courtesy accidentals, transposing instruments, musica ficta, leger lines, tie and slur placement, lyric placement, beam placement and so on. You should not have to worry about any layout changes as a result of transposing.   (Nb. I have structured the code such that prefatory staves are not affected by transposition, though plainsong incipits are.)

One side effect of this is that the music layout might change – the new key signature and leger lines may take up more or less space on the page than what was there previously.  This can even affect the number of pages in the score.

Also note, if you transpose to a sharp note you will get a sharp key signature, and vice versa for a flat note.  Compare transposing to ‘ees’ (e-flat) with transposing to ‘dis’ (d-sharp).  You can end up with some very odd key signatures if you try hard enough!

The only thing you might need to change after applying transposition is applying some different clefs to your tweaked score.  The ambitus at the beginning of each stave in your new score will give you an initial idea whether your new pitch suits the existing clefs. Clefs are also very easy to change  - see below.

This has taken a few paragraphs to explain, but it is very simple to use most of the time.

###  2.6. <a name='Clefs'></a>Clefs

These are specified in section 1d.  Look for a line like 

	StaveAClef =  "treble"

The staves in my scores are lettered A, B, C and so on, from the top to the bottom of the system.   This line tells Lilypond to put a treble clef (clef G2) at the beginning of the top stave of the main musical system.

As you’ve probably guessed, you just need to change what’s in the double quotes to change the clef (including the quotes of course). The names you need to know to create most common clefs are as follows:

code you type | clef that gets generated
:--: | :--:
“treble”	| 	G2
“treble_8”	| 	G2 8ve bassa
“bass”		|	F4
“soprano”	| 	C1
“alto”		|	C3
“tenor”		|	C4

So to make the third stave in the system into a “tenor voice” clef, you would use

	StaveCClef =  "treble_8"

There are many other clefs available in Lilypond, but most of them are to do with specialist notation or early music, so those are the main ones for every-day use. Clefs need to be in lower case.

###  2.7. <a name='StaveNames'></a>Stave Names

By default I use the stave name from the source, rather than suggesting what voice-type should sing each line.   This is because you might disagree with my suggestion!  And also because you might be using my edition at a different pitch, to suit different voices.

The stave labels are in section 1d, with the clefs. Look for a line like 

	StaveALabel =  "CANTVS"

Just change what’s in the quotes (and include the quotes) to what you want.  You don’t need to use capitals – so long as you don’t forget the quotes, you can put what you want in here.  

Try to keep the stave names short, or they’ll fall off the left-hand edge of the page!

###  2.8. <a name='Timesignature'></a>Time signature

You shouldn’t normally need to change this, but if you do, it is set in Section 1e. Look for a line like:

	\time 2/1

The first number is the top number in the time signature, and the second is the lower number.  The line above signifies a time signature of two semibreves in each bar. 

It goes without saying that mensural music did not use regular barlines to indicate metre, so the barlines and time signatures in my transcriptions are a matter of interpretation.  You may disagree with them.

To change this, simply change the numbers above. For example to change to four minims in a bar, just use

	\time 4/2

The music will be re-barred from fresh as necessary using your new time signature.  

This section carries a big caveat though.  Occasionally I insert an irregular bar manually, or a time signature change part-way through the music, and these won’t be affected by your new time signature.  In this situation you might need more extensive Lilypond knowledge to produce a neat score.   You may also find the last note is tied over a barline because your barlines aren’t in the same place as mine.

###  2.9. <a name='Keysignature'></a>Key signature

This is very easy to change if you disagree with my key signature (I may have modernised and regularised key signatures from the stave accidentals found in the source).  Look in section 1e for a line like

	\key c \major

(obviously this will change depending on the individual piece).  

Just substitute whatever key signature you want, eg. ‘f \major’ or ‘a \minor’ etc.  Use lower case, no quotes and notice the space before the back-slash.

Note that this is the un-transposed key signature.  If transposition has been applied then the actual key signature you see on the score will be different.   For example if the key signature is c major but the transposition interval is set to ‘d’ (see the transposition section above) then the actual key signature you end up seeing will be D major. 

Similarly if the only reason you want to change the key signature is because you want to transpose the score, then don’t bother changing this: leave it alone and read the Transposition section.  Lilypond will take care of it and put in the right key signature for your new pitch.

A final note is that the key signature has no effect on the pitches in the music. For example changing from f major to c major will remove the b-flat from the key signature, but will not naturalise all the ‘b’ notes in the music.  They will still be b-flats, but notated with accidentals.

##  3. <a name='Whenyoumakeanerror'></a> When you make an error

Sadly one of the inevitable problems of Lilypond’s design is that it is (of course) all too easy to make a typo.  You will then be passing instructions to Lilypond which it doesn’t understand.  If you do this, Lilypond will throw a red error message when you press Ctrl-M, and will probably refuse to produce a PDF output from what you’ve typed.

This will happen sooner or later (probably sooner).  Don’t worry about it.  

Probably you missed out a quote, or a bracket, or you used single quotes when you should have used double or vice versa, or you used lower case instead of capitals or vice versa and so on.

Most Lilypond users spend loads of time looking at and fixing the errors in their code.  Frescobaldi will highlight error lines in red to help you find them.  (Be aware that an error on one line can have a knock-on effect through a whole chunk of the source file, so a single little error can often look much worse than it actually is).

The good news is that if you’re just fiddling with my section 1 then you’re not going to be writing reams and reams of your own code.  Simple substitutions are all you’re probably making, so it’s probably easy to pin-point where you went wrong.  Check my instructions again, and all should become clear. 
However, you do need to follow the instructions here exactly, including every letter, number, bracket, quote,  comma, back-slash and so on.  Lilypond is a markup language and, like any programming, scripting or markup language, it is absolutely unforgiving of even minor errors.  This is the single biggest drawback of Lilypond in my view. 

If my instructions are wrong or ambiguous, do let me know.

##  4. <a name='Finalisingthescore'></a>Finalising the score

Don’t forget to save your changes regularly (Ctrl-S in Frescobaldi).

When you’re happy with your changes, press Ctrl-Shift-P.  This will publish the score to a PDF (and a MIDI file). 

These two new files will have the same name (but different extensions obviously) as your .LY source file, and will be in the same folder as it.  They are your finished product, ready for printing and performing.


##  5. <a name='SomenotesforadvancedLilypondusers'></a>Some notes for advanced Lilypond users

That's basically it as far as basic tweaking is concerned. No need to read the following unless you're a Lilypond veteran, trying to undestand why my Lilypond source code doesn't look like yours :-).

My scores use the completion note head engraver and the completion rest engraver.  This means that barlines can be moved around at will (up to a point, as described above), relying on Lilypond to tie notes.  Mensurstriche scores are also easily supported for those who like that sort of thing, and most of the code you need is already in the layout block. 

Final notes are drawn using Maxima glyphs, but are usually set manually to the length of a single bar in my time signature.

To remove prefatory staves, change the stave labels in the score block to point to the stave label variables, rather than the PrefStave variables currently in use.

Plainsong incipits are self-contained scores, and can be edited as usual.  At the moment, suppressing the note stem engraver makes the horizontal spacing much too narrow, so I am inserting s4 between each note.  Very tiresome, must fix.

Note values can be halved and doubled using Frescobaldi’s Rhythm menu.  Apply the halving or doubling to everything in section 3.  You presumably want to change the time signature after doing this.   Of course, this actually changes the code in the music_lyrics_notes.ly file, unlike most of the other edits in this document.

All pitches are absolute; all rhythms are explicit.  

Sorry, but I don’t conform the the ‘1 bar per line’ convention which seems to be prevalent in Lilypond code.  This is for a few reasons: partly because most of my scores are of mensural music, so bars and barlines are part of the editorial content, not the musical text, and are subject to change after transcription, and partly to try and limit the numbers of lines of the source.  Also, most of my actual Lilypond source is auto-generated and not designed to be human-readable.  You can use Frescobaldi to click around the source of course – I find this quite adequate for making the odd correction.

MIDI instrument is set at the ChoirStaff level using a variable in section 1e.  The default is ‘ocarina’, because I find it the least offensive option on most cheapo GS MIDI synths.  You may disagree, hence the variable.

Any staff annotations or changes part-way through the music (eg. Time signature) will be sitting inside the notes for stave A in section 3 (music_lyrics_notes.ly) only .

Lyrics’ melismata are done using \melisma and \melismaEnd pairs.  Older scores of mine used to use slurs which were then hidden by removing the slur engraver.  I find this approach reduces trial and error when lining up music and lyrics.

Apart from that, everything’s standard Lilypond stuff I think

##  6. <a name='Notesaboutmyeditorialapproach'></a>Notes about my editorial approach

I assume:

* Modern musicians (particularly singers) need modern clefs, explicit underlay, a score at the correct performing pitch, bar lines (not mensurstriche) and bar numbers.

* For rehearsal purposes keyboard players can busk most scores without a reduction, which would take up a disproportionate amount of page space and transcription time, so I don’t provide one.

* Altos can read treble 8ve bassa clefs.

I bracket staves together to indicate that they have near-identical ranges.  It’s up to you to decide whether to allocate similar voice types to them.

I err on the non-interventionist side when it comes to rhythmic note values because they are a good indicator of tempo.  I know some people prefer them halved but leaving 16th century music in its original note values makes the page look less cluttered and removes almost all quaver beaming quandaries (since quavers were very rarely used in practice).  I try to respect mensural proportion relationships, up to a point.  I will not force the issue, especially if the meaning of the mensural proportion signs is ambiguous or disputable.

I don't put 1950's-style slur marks over melismata; and they clutter the page up badly without adding any useful information about how to sing the music.

I retain original stave names, to give a flavour of the voice types possibly held in mind by the composer, while recognising that these were and still are very flexible.

I often provide editions at multiple pitches, perhaps including the publication or manuscript pitch, the likely intended performance pitch (eg. If chiavetti transposition is likely), a suggested viable equivalent modern pitch and the prevailing ‘popular’ pitch if there is one.   I will change clefs to minimise leger lines in each case 

I don’t italicise editorial underlay.  Pre-modern music publications were never very explicit about lyric underlay, so all lyrics are editorial to a certain extent.

I don’t mark accidentals if they are caused by a modernised key signature, or are clearly required by repeated notes in the source.  Only where I have to make an explicit choice do I mark them.

I am not making scholarly critical editions.  I am not a professional musicologist, and I don’t have easy access to academic libraries.  I may be working second-hand from another edition.  I will try and investigate what the source looked like to help you make performing decisions, but I may not have had first-hand knowledge.  If I have not seen the original publication with my own eyes I will say so.

If you are a professional musicologist, and you do have access to primary sources, and you are able to show me a digital copy, I would welcome suggestions and corrections from you, although as [Thomas Morley](https://imslp.org/wiki/A_Plain_and_Easy_Introduction_to_Practical_Music_(Morley,_Thomas)) rather memorably puts it:

> “The paines of making whereof, though they have beene peculier to mee, and onely to mee: yet will the profit redound to a great number. ... But seeing in these latter daies and doting age of the worlde, there is nothing more subiect to calumnie and backbiting then that which is most true & right: and that as there be many who will enter into the reading of my booke for their instruction : so I doubt not but diverse also will read it, not so much for anie pleasure or profit they looke for in it, as to finde something whereat to repine, or take occasionn of backbyting.  
> 
> “Such men I warne, that if in friendship they will (eyther publickly or privately) make me acquainted with any thing in the booke, which either they like not or understand not : I will not onely be content to give them a reason (and if I cannot, to turne to their opinion), but also thinke my selfe highly beholding to them,
>
> “But if any man, either upon mallice, or for ostentation of his owne knwowledge, or for ignorance (as who is more bolde then blinde beyard) do either in huggermugger or openly calumniate that which either he understandeth not, or then maliciously wresteth to his own sense, he (as Augustus said by one, who had spoken evill of him) shall finde that I have a tongue also. : and that *memorium petit*, He snarleth at one who will bite againe, because  I have said nothing without reason, or at least confirmed by the authorities of the best, both schollers & practictioners.”

Have a nice day!
