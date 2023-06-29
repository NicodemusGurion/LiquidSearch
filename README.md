# LiquidSearch
A JavaScript search engine for Jekyll/Liquid powered sites.

# database.json

Put this file in your root directory. On each commit, this file will go through all the posts in site.posts, and index all the words. It creates a json file that contains a list of all posts, with their titles, urls, images and thumbnails (if specified in the front matter). It also generates a key value dictionary of all the words used on the site (except the most common useless words) and in which post they occur. I have trued to keep the file size as small as possible. This json database is then queried by the javascript for fast results.

# LiquidSearch.js

Put this file where you have javascripts. Make sure to link it into the pages where you want to be able to do searches. see the index.html file for example code. The HTML snipplet for the search form contains only a text field and a div for the results. When the user focuses the text field, the JSON database is loaded into memory. As the user types, the javascript makes instant searches in the database and presents the results in the div.

The search function tries to find the posts that contain one or more of the keywords. The more keywords it contains, the higher it is prioritized. If the word is found in a title it is even more prioritized. 

If the last keyword in the text box is incomplete or not found, it will look for keywords that begin with this string, e.g. "ap" will try for "ape", "apple" or "application" and suggest these.
