# Nest-NG

## Changes in the NG edition
- Use of flexbox for better responsiveness on mobile devices
- Use of default strings to de-clutter pelicanconf
- Footer fixed to bottom of screen if the page is smaller than the vertical height
- Hiding tag glyph if there are no article tags
- Added summary to article page
- Added granular Disqus control
- Scrollable code boxes
- HTML meta tag `description` now comes from the `Summary` markdown metadata, instead from the article content

Nest is a theme for [Pelican](http://docs.getpelican.com) 3.5+, a static site generator written in Python.

I initially created this theme for [my blog](https://blog.dzeri.me), but it is supposed to be generic enough to have its own repository.

## TODO:
Fix pagination

## Screenshots

### Homepage

![Nest Index View](homepage.png)

### Homepage with background

![Nest Article View](homepage-background.png)

Add a background image by configuring `NEST_HEADER_IMAGES` parameter in your pelican.conf. Image should be located in `content/images` directory.

### Article

![Nest Index View](article.png)

### Article or page with background

![Nest Article View](article-background.png)

Add a background image by adding `Illustration` custom parameter in your markdown article or page. Image should be located in `content/images` directory.

	Title: Ubuntu Install
	Date: 2015-02-18 16:00
	Category: server
	Tags: ubuntu, kernel
	Slug: ubuntu-install
	Author: Matthieu OLIVIER
	Illustration: background.jpg


## Features

* Featured site header image
* Featured article header image
* **Pygments** syntax highlighting
* **Disqus** support for comments
* **Google Analytics** support
* **MATOMO** support
* RSS and Atom feeds

## Settings

Nest template can be customized by adding parameters to your `pelicanconf.py` file. Template specifics parameters are prefixed with template name.

The header-nav have a fixed heigth of 100px. This is the max size for the logo without css modification.

The min-height for the background header is 360px. The image is displayed using background-size: cover; which scale the background image to be as large as possible so that the background area is completely covered by the background image. If smaller than screen, the image is repeated to fit the background area.

### Pelican.conf example

```python
# NEST Template
THEME = 'nest'
SITESUBTITLE = u'My Awesome Blog'
# Minified CSS
NEST_CSS_MINIFY = True
# Add canonical link element to top page header and all article/author/category/tag page header
NEST_REL_CANONICAL_LINK = True
# Add items to top menu before pages
MENUITEMS = [('Homepage', '/'),('Categories','/categories.html')]
# Add header background image from content/images : 'background.jpg'
NEST_HEADER_IMAGES = ''
NEST_HEADER_LOGO = '/image/logo.png'
# Footer
NEST_SITEMAP_COLUMN_TITLE = u'Sitemap'
NEST_SITEMAP_MENU = [('Archives', '/archives.html'),('Tags','/tags.html'), ('Authors','/authors.html')]
NEST_SITEMAP_ATOM_LINK = u'Atom Feed'
NEST_SITEMAP_RSS_LINK = u'RSS Feed'
NEST_SOCIAL_COLUMN_TITLE = u'Social'
NEST_LINKS_COLUMN_TITLE = u'Links'
NEST_COPYRIGHT = u'&copy; blogname 2015'
# Footer optional
NEST_FOOTER_HTML = ''
# index.html
NEST_INDEX_HEAD_TITLE = u'Homepage'
NEST_INDEX_HEADER_TITLE = u'My Awesome Blog'
NEST_INDEX_HEADER_SUBTITLE = u'Smashing The Stack For Fun And Profit'
NEST_INDEX_CONTENT_TITLE = u'Last Posts'
# archives.html
NEST_ARCHIVES_HEAD_TITLE = u'Archives'
NEST_ARCHIVES_HEAD_DESCRIPTION = u'Posts Archives'
NEST_ARCHIVES_HEADER_TITLE = u'Archives'
NEST_ARCHIVES_HEADER_SUBTITLE = u'Archives for all posts'
NEST_ARCHIVES_CONTENT_TITLE = u'Archives'
# article.html
NEST_ARTICLE_HEADER_BY = u'By'
NEST_ARTICLE_HEADER_MODIFIED = u'modified'
NEST_ARTICLE_HEADER_IN = u'in category'
# author.html
NEST_AUTHOR_HEAD_TITLE = u'Posts by'
NEST_AUTHOR_HEAD_DESCRIPTION = u'Posts by'
NEST_AUTHOR_HEADER_SUBTITLE = u'Posts archives'
NEST_AUTHOR_CONTENT_TITLE = u'Posts'
# authors.html
NEST_AUTHORS_HEAD_TITLE = u'Author list'
NEST_AUTHORS_HEAD_DESCRIPTION = u'Author list'
NEST_AUTHORS_HEADER_TITLE = u'Author list'
NEST_AUTHORS_HEADER_SUBTITLE = u'Archives listed by author'
# categories.html
NEST_CATEGORIES_HEAD_TITLE = u'Categories'
NEST_CATEGORIES_HEAD_DESCRIPTION = u'Archives listed by category'
NEST_CATEGORIES_HEADER_TITLE = u'Categories'
NEST_CATEGORIES_HEADER_SUBTITLE = u'Archives listed by category'
# category.html
NEST_CATEGORY_HEAD_TITLE = u'Category Archive'
NEST_CATEGORY_HEAD_DESCRIPTION = u'Category Archive'
NEST_CATEGORY_HEADER_TITLE = u'Category'
NEST_CATEGORY_HEADER_SUBTITLE = u'Category Archive'
# pagination.html
NEST_PAGINATION_PREVIOUS = u'Previous'
NEST_PAGINATION_NEXT = u'Next'
# period_archives.html
NEST_PERIOD_ARCHIVES_HEAD_TITLE = u'Archives for'
NEST_PERIOD_ARCHIVES_HEAD_DESCRIPTION = u'Archives for'
NEST_PERIOD_ARCHIVES_HEADER_TITLE = u'Archives'
NEST_PERIOD_ARCHIVES_HEADER_SUBTITLE = u'Archives for'
NEST_PERIOD_ARCHIVES_CONTENT_TITLE = u'Archives for'
# tag.html
NEST_TAG_HEAD_TITLE = u'Tag archives'
NEST_TAG_HEAD_DESCRIPTION = u'Tag archives'
NEST_TAG_HEADER_TITLE = u'Tag'
NEST_TAG_HEADER_SUBTITLE = u'Tag archives'
# tags.html
NEST_TAGS_HEAD_TITLE = u'Tags'
NEST_TAGS_HEAD_DESCRIPTION = u'Tags List'
NEST_TAGS_HEADER_TITLE = u'Tags'
NEST_TAGS_HEADER_SUBTITLE = u'Tags List'
NEST_TAGS_CONTENT_TITLE = u'Tags List'
NEST_TAGS_CONTENT_LIST = u'tagged'
# Static files
STATIC_PATHS = ['images', 'extra/robots.txt', 'extra/favicon.ico', 'extra/logo.svg']
EXTRA_PATH_METADATA = {
    'extra/robots.txt': {'path': 'robots.txt'},
    'extra/favicon.ico': {'path': 'favicon.ico'},
    'extra/logo.svg': {'path': 'logo.svg'}
}
# Matomo tracking (optional)
MATOMO_SSL_URL = 'https://example.com'
# Not needed if SSL URL provided
MATOMO_URL = 'http://example.com'
MATOMO_SITE_ID = 1
```

### Disqus activation

`SITEURL` and `DISQUS_SITENAME` must be set in `publishconf.py` and/or `pelicanconfig.py` to activate the Disqus comment system:

```python
SITEURL = 'https://www.molivier.com'
DISQUS_SITENAME = 'molivier'
```

You can enable/disable comments on a per-article basis, by using the `Comments` metadata keyword, with either `true` or `false`.
The default can be set in your config file by using the `DEFAULT_METADATA` dictionary.


## Third-party assets

The theme uses external softwares, scripts, libraries and artworks:

* [Bootstrap](http://getbootstrap.com/) 3.x.x
* [Open Sans Font](http://www.google.com/fonts/specimen/Open+Sans)
