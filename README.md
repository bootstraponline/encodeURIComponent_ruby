encodeURIComponent for Ruby
=======================

A port of V8's URIEncodeComponent to Ruby.

Based on `r11482` of V8's [SVN repository](https://code.google.com/p/v8/wiki/Source).

# Why use this?

* There's no other complete implementation of JavaScript's encodeURIComponent for Ruby that I'm aware of.
* Based on the excellent V8 code used in Chrome.

# What about CGI.escape?

CGI.escape is not the same as encodeURIComponent.

```
CGI.escape('hi there')
 => "hi+there"

encodeURIComponent('hi there')
=> "hi%20there"
```

The encoding results are quite different.
```
encodeURIComponent(" ~!@#$%^&*(){}[]=:/,;?+'\"\\")
"%20~!%40%23%24%25%5E%26*()%7B%7D%5B%5D%3D%3A%2F%2C%3B%3F%2B'%22%5C"

CGI.escape(%q( ~!@#$%^&*(){}[]=:/,;?+'\"\\))
+%7E%21%40%23%24%25%5E%26%2A%28%29%7B%7D%5B%5D%3D%3A%2F%2C%3B%3F%2B%27%5C%22%5C
```

CGI even has differences between ruby versions.
```
CGI.unescape('%C2%A3')
 => "\302\243" # 1.8.7
 => "£" # 1.9.3
```

- http://xkr.us/articles/javascript/encode-compare/
- http://stackoverflow.com/questions/2858345/ruby-equivalent-to-javascripts-encodeuricomponent-that-produces-identical-outpu
- http://www.ruby-forum.com/topic/183017