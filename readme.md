# latex-beamer like slides with revealjs and pandoc

You can make slides that look (moreless) like beamer, but as html files, so they can be seen in any browser, thanks to revealjs and pandoc.

Besides, by using markdown as a source, you can use a more efficient workflow.

Here you have a `beamer.css` file that tries to look similar to a beamer presentation. If you copy it to your `/reveal.js/css/theme/` directory, you can use it in your reveal slides.


Look at `example.md` to see how to create the corresponding markdown file.

Once created your markdow file, the html file can be created with:

```
pandoc example.md -o example.html \
       -t revealjs \
       --katex=./katex/  \
       --standalone \
       -V theme=beamer \
       -V transition=none  \
       -i --slide-level 2 \
       --self-contained
```

The parameters are the following:

- `example.md` is the markdown file that you wrote.
- `-o example.html` stablishes the name of the output file (in this case, you will create a example.html).
- `-t revealjs` means the format of the output, in this case, it is reveal.js slides. You can choose plain html, latex, beamer, pdf and many others (run `pandoc --list-output-formats` for a full list)
- `--katex=./katex/` tells pandoc to use the katex available in the `/katex/` directory to render the latex fragments (only makes sense for html type outputs). If you just use `--katex` it will try to get it from internet.
- `--standalone` Is to create a full html file (with the header and footer). Without it, you would get just the html code that can be embedded in other web documents.
- `-V theme=beamer` sets the theme to beamer. It needs a file called `beamer.css` in `/revealjs/css/theme/` (revealjs specific).
- `-V transition=none` tells revealjs to use no visual transition between slides. Other possible values are `fade`, `slide`, `convex`, `concave` or `zoom`.
- `-i` This tells reveal to show the list items one by one. If you prefear to show them all at once, you can skip this parameter.
- `--slide-level 2` Tells revealjs that new slides are created with `##` (This way you can use `#` for slides with a big centered title for new sections).
- `--self-contained` Tells pandoc to embed all the needed data (javascript, style, images and videos) in a single html file. Without it, you would get a smaller file, but it would need the rest of the files to render correctly.
