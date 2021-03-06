Could RewriteRails Make ActiveRecord Mundane?
===

A thought crossed my mind: Many people complain about [Ruby on Rails](http://rubyonrails.org/ "Ruby on Rails")' use of "magic," things like all of the automatically generated methods and so forth. The most obvious cases are controllers and [ActiveRecord](http://api.rubyonrails.org/classes/ActiveRecord/Base.html "Class: ActiveRecord::Base") models (from here in I'll call these "models" even though we both know you can have models that are not ActiveRecord instances).

Consider model classes. A few declarations... `acts_as_inscrutable`, `acts_as_magical`... And the model class gains a whole bunch of class and instance methods, plus often a whole bunch of `method_missing` behaviours that "behave like" methods. Some people complain it is hard to figure out what methods a model really has.

What if [RewriteRails](http://github.com/raganwald/rewrite_rails "raganwald's rewrite_rails at master &mdash; GitHub") were to rewrite ActiveRecord model class declarations to "mundane-ify" these magical methods? In other words, after a class has been loaded and all of the magic performed, RewriteRails writes out a `.rb` file that has the source code for all of the magic methods as if the programmer had written them in by hand.

This `.rb` file can be placed somewhere that Rails can't find it, this is a case of documentation. Now a programmer can read the mundane-ified `.rb` file to get an idea of what methods the model class actually has.

Just a thought...

----
	
Subscribe to [new posts and daily links](http://feeds.feedburner.com/raganwald "raganwald's rss feed"): <a href="http://feeds.feedburner.com/raganwald"><img src="http://feeds.feedburner.com/~fc/raganwald?bg=&amp;fg=&amp;anim=" height="26" width="88" style="border:0" alt="" align="top"/></a>

Reg Braithwaite: [Home Page](http://reginald.braythwayt.com), [CV](http://reginald.braythwayt.com/RegBraithwaiteGH0109_en_US.pdf ""), [Twitter](http://twitter.com/raganwald)