#Towards Swash, a new CLI-descended UI paradigm for the open web.
##(Status: Planning, requirements assessment)

Core idea: use HTML5/CSS3/ECMA.next to build nex-gen UI for CLI lovers who are lost in a gooey, touchy, mobile cloud. I'm going to call this project 'swash', and apps designed around swash are going to be called 'buckles'. (Groan: "It's a swash buckle! I'm a swash buckler!")

The CLI has stuck around for several reasons.

 - Right place, right time (MS failed; Linux won; FOSS came of age; Apple converted to the Church of BSD...)
 - Muscle-memory lock-in. I've tried to leave Vim more times than I can remember.
 - Shell is hard. Therefore it tends to attract technically minded-people. But technically-minded people are, in Internet terms, high-status. 'Monkey-minded network effects, i.e. status.'
 - Real network effects. Think of how much work you get done with SSH.
 - Shell has a finite set of rules that generate just the right kind of learning curve. (Expand/explain. Points: there is always more to learn....; it's never impossible, just hard; TODO insert proper reference to 'A Theory of Fun for Game Design' )
 - Epistemic stability. The knowledge I gained fifteen years ago viz. shell has stayed relevant a lot longer than most of my other tech skills. I've had to learn, unlearn, or relearn countless GUIs in that same period.
 - Accountability. The CLI generates a transcript.
 - Compatibility with the most important protocol of all, spoken language. Ever try to guide someone over the phone with a GUI? Tech support is a lot easier for shell because you can just say 'type in foo and tell me what it says back'.
 - Creativity always flourishes where there are restrictions. For example, iambic pentameter. The shell introduces its own harsh restrictions on what is possible. This is why it's so exciting when you see, e.g., sparklines being implemented in unicode -- it's not because sparklines are intrinsically difficult, it's because it's a way of doing sparklines _within the current game's rules_ and for whatever reason, that is pleasing to humans.
 - Standardization. Shell is a language shared with computers -- your CLI actions are actually a form of coding. This is not true of GUI languages -- the computer doesn't depend on the same mechanism for its internal interactions as you do to interact with it. I.e., there is a 'translation' step. Because CLI is untranslated, and because the same behavioural pathways are used by and this gives it more 'inertia' than languages that are only shared by humans. The computer has to speak shell too, so the grammar is rigid and can change only if the vast lock-in of shell scripts is dismissed. (TODO make this sentence sound good)
 - Distraction prevention. The single-tasking nature of CLI makes it harder to schlep ineffectually between several competing tasks.
 - The shell abstracts text away from irrelevancies like formatting. There is literally nothing else to see except what's on your screen -- no subtle details to worry about. 16 colors is already too many, I'd say about 12 more than optimal.
 - Isomorphism between surface expression and underlying fine structure of computing. Shell reflects the way a computer _is_. A GUI often apologizes for it.
 - The utter, utter universality of the keyboard, right up until the iPhone.
 - Codebase stability. It just works.

The CLI is threatened because:

 - Keyboards are now optional.
 - Touchscreen devices make it harder to use a shell.
 - Learning shell requires considerable up-front temporal investment.
 - It won't be high-status forever; there are many hard-to-master techniques that do not invite respect because their masters are themselves no longer high-status. E.g. haberdashery; accounting with Roman numerals; etc. If the developing world comes online with the promised half-billion coders, development will be cheap, and the shell will be about as sexy to learn as hairdressing.
 - The web is also a text-based, transcript-friendly UI, and threatens the shell on those points. In effect, it's competing in the same space.
 - The shell is butt-ugly and hard-to-read. It takes years before you stop noticing how hideous it is, and even then it takes an act of transcendent patience. Since everything else on the Internet is always getting slicker and prettier (even if not more useful) the shell will seem even uglier by default. This will constrict the supply of new users and eventually existing users will age out. Yes, I _know_ that people have been saying this will happen next week for the past twenty years; but they've also been saying that the book would die for fifty, and then suddenly (hello, Kindle) it did. Punctuated equilibrium is sometimes an interrobang.
 - The influx of mobile devices (esp. those with cameras and high-res displays) mitigates the importance of being text-based, because people are now far better at sharing images with one another, moving, interactive or otherwise. You can literally pull up your comp's desktop (or the desktop of someone you're helping) on your LTE tablet while you ride the train. Compatibility with spoken language is less important when you have access to more than just spoken language.
 - Increasing stability of other stacks with similar ranges; e.g. JavaScript is (arguably) cleaner than Bash, and much more widely understood.

#So what to do? Hybridize!
Here's a good way of merging the best of the CLI with the current best-of-show interface, the Web. There are a lot of synergies. Well, it's showtime, synergy!

First, start with typography. Typography is hundreds of years of condensed research into how to present text to people. Modern systems like OTF and SIL Graphite (especially the latter) allow the font itself to contain a lot of intelligence about formatting, and this expands the range and comfort of Swash. Better yet, OTF is baked into almost all browsers, and SIL Graphite is available to XUL apps and thus to Firefox. (you do for some reason have to enable it in about:config first; why? TODO research)

Second, embrace markup. Allow Markdown-formatted 'usage' messages, for starters. Allow pictures, allow form fields. Allow manipulation of what's on-screen via a DOM. In short, allow anything that there isn't a damn good reason to prohibit.

Third, embrace JavaScript. It's time.

But-but-but, I hear you say. 'My favourite scripting language isn't Javascript, it's Python/Ruby/Perl/Haskell/Befunge/whatever! Let's remake the shell using that instead.'

I love Python too, but as the old editing adage says, 'kill your darlings.' Which is to say that as a writer you can make any corpus of text stronger by removing your favourite passages, because they probably exist for their own sakes (you put them in because you love them) rather than for the sake of the text (you put them in because they support the text). The same is probably true of software and features. In this project, Python (or similar) is one language too many. Let's keep it around for the stuff it's currently doing, though. May a thousand flowers bloom, but elsewhere.

Fourth, extend JavaScript. JS is a great language, but it is imperfect as a shell. CoffeeScript or (my personal fave) the CoffeeScript/Cocoscript fork called LiveScript are much better candidates, as they are terse. Firstly, readability is obviously less important than writability in a shell scenario because that's what the user is doing most of the time; secondly, because we control the presentation environment, we can build intelligence into the fonts using Graphite and OTF such that , e.g, '`->`' has a ligature which is an actual honest-to-God arrow, and that means it's more readable. A _lot_ more? I don't know, let's find out!

Fifth, embrace blog-style ordering. On a terminal, the past is at the top and the most recent line is at the bottom of the screen, but on a blog this is reversed: each section is read top-to-bottom, but sections are ordered most-recent-first. So at the micro scale, flows down (oldest first), but in the big picture, it flows up (oldest last). This has the felicitous side-effect of preventing output from various commands from smushing together in presentation, as currently often happens in a terminal. Let's welcome this change.

Sixth, use infinite-scroll techniques, and make history-preservation, both on the browser and the server, an absolute requirement. I don't want to _guess_ at what happened in my session. I want to _know_.

Seventh, use form controls, images, movies, and anything else you can stuff in an HTML document as the interface to your CLI app. Imagine a usage box that presented each flag as a link, and when you click the link, it gets added to your input.

Eighth, poach what is there to be poached from the highly interesting acme editor. The idea of attempting to execute an executable on the basis of whatever word the cursor is in could be refitted to execute functions, URLs, JavaScript expressions, Swash expressions.... After all, isn't acme basically just ad-hoc hypertext, the same way that Go offers ad-hoc interfaces? A good idea with many uses, aye!

Ninth, augment the file system with the HTTP ecosystem. Semantic point: executing a directory, e.g. http://undoware.ca/foo/, might load a page *or* show a listing. However, it would be possible to make some web servers reply to a request like http://undoware.ca/foo.opml, even if there is another document at http://undoware.ca/foo/. This extends the most important shell paradigm -- the current directory -- to the web.

Tenth, include the ability to specify HTTP parameters on the command line:

`$ get http://undoware.ca/some-file
 $ post 'foo' some_new_file
 $ delete some_new_file
 $ put 'foo' some_file
 $ ./some\_file ` # this one is not in HTTP

Eleventh, use the wideness of current widescreens to show zoomed-out, partially greeked version of the entire document thus far, with clickable 'panels' corresponding to the results of commands. Think of a mashup between Sublime Text 2 and the 'pages' column in, e.g., evince or Acrobat Reader.(The 'pages' correspond to Swash buckles.)

Also present the user with snippets panels, a history palette, etc. And make sure they're all accessible from the command line!

Twelfth, make sure that whatever is presented on the screen is made static and as plain as possible when the command to which it was a response is no longer the most recent. For example, if I filled out a form a few minutes ago, I should be able to scroll back up and copy my entries with a simple drag-select-and-right-click. I should not however be able to edit them, and they should not appear in enabled form controls (because these are a visual cue that editing may be performed.).

Thirteenth, make sure that the buckles are all responsive. On a touch screen I want to see a verbosity slider, dammit, rather than have to futz around with a virtual keyboard to generate '-vvvvvv' or whatever.

If you want to help out, fork and start working on this. Pull requests accepted if I like them.