# min_night

Blogs are for reading and sharing. This theme tries to make both of those better.

`min_night` is built on top of [Minimal](https://github.com/calintat/minimal), and keeps a lot of the cool original features:

- Bootstrap
- GoogleAnalytics
- GoogleFonts
- FontAwesome
- HighlightJS


It also gets a bunch of new add-ons:

- A night-mode toggle, with HTML5 storage to remember view preferences
- OpenGraph and TwitterCard meta tags for upgrading your social sharing
- Favicon support via the [RealFaviconGenerator](https://realfavicongenerator.net/)
- A site logo for index.html (headshot, hexsticker...its up to you)
- A tags/categories list page template from [Xmin](https://github.com/yihui/hugo-xmin)
- Updated tag labels to hyperlinks (categories too)
- Tweaked list templates for posts and projects

A live demo is available [here](https://natedayta.com).

## Installation

Installing Hugo themes as submodules is best.

This is how you can get starting with `min_night` using the [QuickStart tutorial](https://gohugo.io/getting-started/quick-start/). Run each line individually.

```bash
hugo new site quick
cd quick
git init
git submodule add https://github.com/nathancday/min_night.git themes/min_night
cp -r themes/min_night/exampleSite/ .
hugo server -D
```

Now your brand new site is being served locally at `localhost:1313`.

Submodules are better because it makes updating the theme easier for future you.

```
$ git submodule update --remote themes/min_night
```

Personally I use this theme via the `R` package `blogdown`, and you can too, like this:

```
library(blogdown)
new_site(theme = "nathancday/min_night")
```

## Configuration

To configure most of the customizations in this theme all you need to do is edit the parameters in `quick/config.toml`.

### Colors

```toml
[params]
    accent = "#006264"
    backgroundColor = "#f5f5f5"
```

- `accent` changes the color of the navbar and footer in day-mode and the color of the body background of your site in night-mode. Dark colors work best.

- `backgroundColor` changes the background color of the body. The default is light grey for easy eye reading.

Always use hex codes.

### Fonts

```toml
[params]
    font = "Mina"
```

This theme uses [Google Fonts](https://fonts.google.com), so go nuts.


### Syntax highlighting

```toml
[params]
    highlight = true
    highlightStyle = "solarized-dark"
    highlightLanguages = ["r", "python", "bash"]
```

The theme supports syntax highlighting thanks to [highlight.js](https://highlightjs.org), which is turned on by default. Checkout out the available palette options [here](https://highlightjs.org/static/demo/). Note `highlightStyle` param should be hyphen-separated lowercase.

Make sure your main languages render well and keep control on the languages that get special highlighted.

For best aesthetics with dark-mode, I reccommend choosing a light background style that matches your `accent` color. 

### Favicons

This theme comes equipped with stock favicons modeled as hex stickers.

To update those, pick out an image and head over to [RealFaviconGenerator](https://realfavicongenerator.net/). Go through their build process and append the path `/img/favicon/` at the last step when you download. Just unzip and drop all of the new files in `quick/static/img/favicon/`. Now you have favicons for everything from tablets to tiles, that's tight.

### Site Logo

The site logo defaults to using the 192x192 Android favicon but you can change the path for `logo` param in `config.toml`. This could be a headshot, another hex-sticker or something completely different, but if you want to change the image dimensions drastically, you may have to tweak `layouts/index.html` directly to get a good result.

### Social Sharing

You must change `baseURL` to your current domain for this feature to work properly.

```toml
baseURL = "your_domain.com"
```

The current set up has two TwitterCard/OpenGraph options depending on the params you specify in your post's front matter. If you add the param `twitter_img` to a post, with the valid image path, then a summary card with large image will be shown. If you don't provide `twitter_img` then a summary card with the site logo will be shown instead. For best scaling large image summary wants a 2:1 ratio image and regular summary wants 1:1. The post `exampleSite/creating-a-new-theme.md` has been tweaked to include these new params, so you can template and test off of that.

The summary description will use the one provided in a post's front matter if it exists or use the generic site description from `config.toml`. You should also adjust the `twitterAuthor` and `twitterSite` params in `config.toml` to point to your account. You can check how your cards are rendering once your website is being publish with the [TwitterCard Validator](https://cards-dev.twitter.com/validator).

### Font Awesome

Font Awesome v5 icons are supported. The syntax for using these icons has changed with the version update. You must now include the full name of the icon e.g. `far fa-twitter` which adds a tag that specifies the weight of the icon used.  Note that only free icons are supported by default.  If you are a Font Awesome Pro user, you can add your website as a new project which will generate the code necessary to reference the pro CDN.  Use the HTML code that is generated to replace that in the file at layouts/partials/css.html. Learn more in the [Font Awesome docs](https://fontawesome.com/how-to-use/on-the-web/referencing-icons/basic-use).

### [Coral](https://github.com/coralproject/talk) (formarly Talk)


[Coral](https://github.com/coralproject/talk) is set of tools back by Mozilla, to make website commenting better. It is aimed at the news industry and has a lot of features for moderating a community, including abilities to mute annoying voices, set up specific notifications and access detailed commentor histories.

While Coral can be viewed as alternative to Hugo's built-in support of Disqus, but it is definately geared towrds larger sites and requires extra tech infrastructure. Inorder to run Coral you will need to install additional software on your server, but this theme includes partial layouts for easily adding the required JS + HTML into your pages.

To enable the parts for Talk v4 and Coral (Talk v5 or later) edit your `config.toml` file like this:

```toml
talkHost = "talk.example.com" # TalkV4
coralHost = "coral.example.com"
```

Make sure you comment out (or delete) the `disqusShortName` field in `config.toml` to prevent multiple comment plugins being included. And make sure your host has SSL encryption (eg https://example.com) enabled becasue Talk/Coral requires it.

Talk/Coral templates are graciously contributed by @mzch

## Going forward

This theme is something I enjoy and hope you do to.

If you get unexpected behavior post an issue and try to keep it as minimal as possible. Ideally bug reports would be reproducible using the [QuickStart tutorial](https://gohugo.io/getting-started/quick-start/) plus whatever changes cause the problem.

Pull requests are literally the best thing since ever, so if you have the idea (and the time) to add something to `min_night` do it! I promise I will respond quickly.

Happy blogging!

