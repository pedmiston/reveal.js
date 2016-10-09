# Building hakimel/reveal.js presentations

This is a personal fork of reveal.js that ignores the "index.html" file that is necessarily in the main, upstream repository (hakimel/reveal.js). I want to ignore this file because I write my presentations in markdown (not html) and output the results as html using pandoc. This way when I'm writing a presentation I can build it outside of this repository, and place it in a clone of this repo as "index.html", and I don't have any `git` warnings about modified files. To do this properly, you need to clone this repo as a submodule.

    new-presentation/$ touch presentation.md  # my new presentation in markdown
    new-presentation/$ git add presentation.md && git commit -m "Started my presentation"
    new-presentation/$ git submodule add git@github.com:pedmiston/reveal.js  # ... git submodule init && git submodule update ?
    new-presentation/$ pandoc -s -t revealjs -o reveal.js/index.html presentation.md  # build into the submodule (untracked!)
    new-presentation/$ ln reveal.js/index.html presentation.html  # I like presentation.html right by presentation.md
    new-presentation/$ open presentation.html

Now you don't have to track any html files!

    new-presentation/$ echo presentation.html >> .gitignore
