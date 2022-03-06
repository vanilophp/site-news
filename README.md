# Vanilo E-commerce News

To read the news from this repo, go to: [vanilo.io/news/](https://vanilo.io/news/)

This repository contains the source markdown files and images
for Vanilo News.

## Contributing

Feel free to contribute by submitting new articles via pull requests.

**Acceptance Criteria** for Submitted Articles:

- Topic must be relevant to Vanilo.
- The article must be in the root folder of the repo.
- The article must be in valid markdown format with `.md` file extension.
- The filename must be in `kebab-case` (ie. all lowercase letters, no underscore, hyphens for word separator, eg.: `wengado-released-paddle-plugin-for-vanilo.md`).
- The filename shouldn't start with `news` (it's already on the path).
- File assets must be in a separate folder matching the filename of the article, eg.: `wengado-released-paddle-plugin-for-vanilo/screenshot1.jpg`.
- The article must use proper English grammar.
- The file must begin with a [YAML front matter](https://jekyllrb.com/docs/front-matter/) section containing at least the following data:
    - `title`": the title of the article in [Title Case](https://en.wikipedia.org/wiki/Capitalization#Title_case).
    - `excerpt`: Short (1-2 sentences) summary of the article. Gets shown in the article list.
    - `date`: The date of the article in `YYYY-mm-dd` format, eg.: `2019-04-21`.
- The article must not begin with the title/h1, because it gets added from the title from the yaml front matter section.
- An image must be added having the following properties:
  - JPEG
  - 795x442 pixels
  - placed in the `img/` folder
  - having the same filename as the article itself, but having `.jpg` extension instead of `.md`

### Example Article

~~~markdown
---
title: Vanilo 3.0 Released
excerpt: Vanilo 3.0 has been released with Shipments, Variants and many other features. See what's new.
date: 2022-02-28
tags: [Releases, News, 'Vanilo 3']
---
Vanilo 3.0 has been released with the following features:

- Shipments
- Links: for product relations like upsell, similar and variant links

You can use code blocks to illustrate the content:

```php
//in app/Providers/AppServiceProvider.php:
public function boot($app)
{
    // This is BS, but this is a demo-demo article, ok? ;)
    $app->appShell->theme->setPrimaryColor('#4349dd');
}
\```

> Use Markdown features like blockquotes.

## Use Headings To Partition The Article

It helps people to understand your article better.

### Use Multiple Heading Levels

Avoid using H1 since that's the title of the article, start from H2 for the major sections of your
article.

Also don't over-articulate, using more than 2-3 levels is usually unnecessary.

Have fun!
~~~
