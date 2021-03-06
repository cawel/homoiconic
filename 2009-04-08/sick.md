I'm Sick of This Shit
===

Yesterday, I wrote on Twitter: "Sick of this shit: [http://tinyurl.com/dmnxhu](http://blog.teksol.info/2009/03/27/argumenterror-on-number-sum-when-using-classifier-bayes.html "ArgumentError on #Sum When Using Classifier")." To paraphrase François, the Classifier gem adds a #sum method to the Array class in Ruby. So does Rails' ActiveSupport. This is a problem which requires some hideous forking and patching to resolve.

[![(c) 2005 Karoly Lorentey, some rights reserved](http://farm1.static.flickr.com/24/43762220_6533e951a6_d.jpg)](http://www.flickr.com/photos/lorentey/43762220/ "(c) 2005 Karoly Lorentey, some rights reserved") 

I ran into the exact same problem when implementing [andand](http://andand.rubyforge.org/ "Object#andand"). I wrote a `BlankSlate` class. Some other gems introduce their own BlankSlate classes. So what does andand do? It checks to see whether a BlankSlate class exists when it is instantiated, and it only defines its own if you don't already have one. It doesn't arrogantly assume that you want its own definitions of everything. (Lest you think I have discovered the solution to the problem, consider what happens if someone defines a BlankSlate class that models writing tablets instead of being a lightweight Object superclass, then loads andand. Interesting.)

James Iry's [response on Twitter](http://twitter.com/jamesiry/statuses/1471207766 "Twitter / James Iry: @raganwald dynamic meta-pr ...") was to suggest that "dynamic meta-programming is a very sharp double edged sword." James, yes. And I like that metaphor, because swords are so two millennia ago. James' metaphor captures the cultural problem beautifully.

Look, overwriting the #sum method on Array is a lot like overwriting the value of a variable. This is a solved problem in other programming domains without abandoning programming. For example, in functional programming you can't mutate variables. I can close my eyes and imagine a language where you can extend classes but not change them. In databases you have transactions with isolation between them. I can close my eyes and imagine a language where the Classifier gem has its version of the Array class, Rails has its version, and the two never conflict with each other.

The problem here, the thing that irritates me, is that we are using these medieval tools for meta-programming. The current Ruby Way is a lot like using GOTO. Sure, it works, and perhaps it ought to exist under the covers. But in my lifetime I have witnessed our ability to progress from GOTO to structured programming to mapreduce. Each step along the way has given us an ability to raise the functionality to maintainability ratio.

Likewise over in La-la-lisp land we have moved from naked recursion to recursive combinators. Combinators make our programs easier to understand and reason about. Naked recursion is GOTO dressed up in a scholar's mortar and gown. Likewise naked monkey-patching is GOTO dressed up in... Well, it isn't really dressed up, it's more baggy pants performing a frontside grab.

[Metaprogramming is beautiful.](http://weblog.raganwald.com/2008/07/my-analyst-warned-me-but.html "My analyst warned me, but metaprogramming was so beautiful I got another analyst") Now that we have embraced its beauty, let's invest some time and energy taking it to the next level, finding ways to apply abstractions and constraints to it so that we can benefit from it without falling into these entirely avoidable contretemps. I've taken one swing at the bat: I think many of the extensions people have added to core classes (including #andand) ought to be syntactic abstractions rather than methods, so I wrote [rewrite](http://github.com/raganwald/rewrite/tree/master "raganwald's rewrite at master - GitHub").

Now its your turn. Dazzle me.

---
	
Subscribe to [new posts and daily links](http://feeds.feedburner.com/raganwald "raganwald's rss feed"): <a href="http://feeds.feedburner.com/raganwald"><img src="http://feeds.feedburner.com/~fc/raganwald?bg=&amp;fg=&amp;anim=" height="26" width="88" style="border:0" alt="" align="top"/></a>

Reg Braithwaite: [Home Page](http://reginald.braythwayt.com), [CV](http://reginald.braythwayt.com/RegBraithwaiteGH0109_en_US.pdf ""), [Twitter](http://twitter.com/raganwald)