# EasyStaticSite

EasyStaticSite is a static site generator that is dead-simple to install and use: Just download and run it, and it will open a browser-based admin section. Written in Python, it has no dependencies other than the Python interpreter already installed on your system (if you use OS X or Linux), and its admin section has no external JavaScript dependencies, meaning you can use it offline.

![Screenshot](https://raw.githubusercontent.com/codenhagen/easystaticsite/master/screenshot.png)



## Features

- Easy post/page editing. Use the WYSIWYG editor or the raw HTML one.
- Extremely simple templating system.
- Use offline; publish once online.
- Easy menu editing.
- Configurable, localized date format.
- Export to JSON.



## Limitations

- The WYSIWYG editor is limited feature-wise.
- EasyStaticSite has in-browser editing, so if you prefer to compose posts/pages in your favorite editor, EasyStaticSite is not for you.
- No built-in commenting system (but you can use one of the free comment services. Adding their JavaScript to your template is easy).
- No tags, categories, or search function.



## Requirements

- Python 2.7+ or 3+.



## Install

##### OS X or Linux
- Download easystaticsite
- Make it executable: `chmod +x easystaticsite`
- Put it somewhere on your path: `sudo mv easystaticsite /usr/local/bin/`
- Run it: `easystaticsite`

##### Windows
- [Install Python](https://www.python.org/)
- Download easystaticsite
- Run it: `python easystaticsite`



## FAQ

##### Where can I find the template file?
~/easystaticsite/template.html

##### Which template tags can I use?
Before checking out this list, please take a look at the template - it is fairly self-explanatory.
- `{{ title }}` goes between `<title>` and `</title>`. Optional.
- `{{ site_name }}` outputs your site name (configurable on the Settings admin page). Optional.
- `{{ page_menu }}` outputs the page menu (configurable on the Menu admin page) as `<li>` elements. Optional.
- `{{ post_loop_start }}` does not output anything, but indicates that this is the start of the post loop, i.e. the part that is repeated for each post on the page. **Mandatory**.
- `{{ post_loop_end }}` does not output anything, but indicates that this is the end of the post loop. **Mandatory**.
- `{{ post_id }}` outputs the numerical ID of the post. Must be inside the post loop. **Mandatory**.
- `{{ post_url }}` is the file name of the post/page; i.e. this-is-a-test.html. Must be inside the post loop. Optional.
- `{{ post_title }}` outputs the title of the post. Must be inside the post loop. Optional.
- `{{ post_date }}` outputs the date according to the date format you have specified on the Settings admin page. Must be inside the post loop. Optional.
- `{{ post_body }}` outputs the body of the post or page. Can contain HTML. Must be inside the post loop. Optional.
- `{{ archive_link }}` outputs the "older entries" link; configurable on the Settings admin page. **Mandatory**.
- `{{ generator_name }}`outputs the name of the generator; EasyStaticSite. Optional.
- `{{ generator_url }}` outputs the URL to EasyStaticSite's home page. Optional.

##### Can I put my own static files (e.g. CSS files, images, etc.) or folders inside the document root without EasyStaticSite overwriting/deleting them?

Sure. EasyStaticSite only writes .html files, so files with any other extension are okay. In case you need to manually place a .html
file there, just make sure it doesn't have the same name as one of the post/page slugs.

##### How do I add images to my posts/pages?

EasyStaticSite has no interface for that, so you will have to manually copy the image(s) to the document root (~/easystaticsite/web) and then,
when editing a post/page, select the HTML editing tab and insert an `<img>` tag in the code.

##### What files/folders does EasyStaticSite store on my system?
- Config file: ~/.easystaticsite_config.json. You should not need to edit this by hand; instead, go to the Settings admin page.
- Site folder: ~/easystaticsite. Contains the template, the post/page database and the document root folder (named "web"). You can change the location of the site folder on the Settings admin page.