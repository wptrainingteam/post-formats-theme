# Post Formats (Theme)

## Description

What are [Post Formats](http://codex.wordpress.org/Post_Formats "Post Formats"), how can you use them, and how do you develop Post Formats? This step-by-step walkthrough will give you an understanding of what Post Formats are and how to create your own.

## Prerequisite Skills

*   Basic knowledge of HTML/CSS/PHP
*   Basic knowledge of installing and activating WordPress themes
*   Understanding of how folders and files are structured
*   Ability to edit files with a text editor

## Objectives

*   Students will create each post format using a default WordPress theme
*   Students will enable Post Format support on a theme that does not yet have Post Formats enabled
*   Students will style each Post Format type

## Assets

*   WordPress installed locally
*   [Twenty Thirteen](http://wordpress.org/themes/twentythirteen) theme installed (all post formats done and styled)
*   [Twenty Twelve](https://wordpress.org/themes/twentytwelve/) theme installed (to demonstrate how to enable and style Post Formats when not already supported by selected theme)
*   Child theme to enable post formats
*   Filler content from Theme Unit Test Data

[alert]It is important that you have Underscores configured as a fully functioning theme, minus the Post Formats, to demonstrate how to configure and style. [/alert]

## Screening Questions

*   Are you familiar with installing and activating themes via the WordPress Dashboard?
*   Do you have at least a basic knowledge of HTML/CSS/PHP?
*   Do you feel comfortable using a text editor to edit code?
*   Will you have a locally or remotely hosted sandbox WordPress site to use during class?

## Teacher Notes

*   Performing a live demo while teaching the steps to make a child theme is crucial to having the material “click” for students.
*   It is easiest for students to work on a locally installed copy of WordPress. Set some time aside before class to assist students with installing WordPress locally if they need it. For more information on how to install WordPress locally, please visit [Installing on a Local Server](https://make.wordpress.org/core/handbook/installing-a-local-server/ "Installing on a Local Server").
*   The preferred answers to the screening questions is “yes.” Participants who reply “no” to all 4 questions may not be ready for this lesson.

## Hands-on Walkthrough

### Introduction: What are Post Formats?

Post Formats have existed in WordPress since 3.1\. However, few themes natively support it, and fewer users implement it. A Post Format is a piece of meta information that can be used by a theme to customize its presentation of a post. The Post Formats feature provides a standardized list of formats that are available to all themes that support the feature. Themes are not required to support every format on the list. New formats cannot be introduced by themes or even plugins. The standardization of this list provides both compatibility between numerous themes and an avenue for external blogging tools to access this feature in a consistent fashion. In short, with a theme that supports Post Formats, a blogger can change how each post looks by choosing a Post Format from a radio-button list. Types of Post Formats include: **Aside** - Typically styled without a title. Similar to a Facebook note update. [![Aside Post Format](http://make.wordpress.org/training/files/2014/08/Screen-Shot-2014-08-01-at-2.02.50-PM-1024x385.png)](http://make.wordpress.org/training/files/2014/08/Screen-Shot-2014-08-01-at-2.02.50-PM.png) **Gallery** - A gallery of images. Post will likely contain a gallery shortcode and will have image attachments. ![Post Format Gallery](http://make.wordpress.org/training/files/2014/08/Screen-Shot-2014-08-01-at-1.59.02-PM-1024x670.png) **Link** - A link to another site. Themes may wish to use the first <a href=””> tag in the post content as the external link for that post. An alternative approach could be if the post consists only of a URL, then that will be the URL and the title (post_title) will be the name attached to the anchor for it. [![Link Post Formats](http://make.wordpress.org/training/files/2014/08/Screen-Shot-2014-08-01-at-2.04.30-PM-1024x295.png)](http://make.wordpress.org/training/files/2014/08/Screen-Shot-2014-08-01-at-2.04.30-PM.png) **Image** - A single image, with or without a caption. The first <img /> tag in the post could be considered the image. Alternatively, if the post consists only of a URL, that will be the image URL and the title of the post (post_title) will be the title attribute for the image. [![Image Post Formats](http://make.wordpress.org/training/files/2014/08/Screen-Shot-2014-08-01-at-2.19.44-PM-1024x573.png)](http://make.wordpress.org/training/files/2014/08/Screen-Shot-2014-08-01-at-2.19.44-PM.png) **Quote** - A quotation. Probably will contain a blockquote holding the quote content. Alternatively, the quote may be just the content, with the source/author being the title. [![Quote Post Formats](http://make.wordpress.org/training/files/2014/08/Screen-Shot-2014-08-01-at-2.21.24-PM-1024x365.png)](http://make.wordpress.org/training/files/2014/08/Screen-Shot-2014-08-01-at-2.21.24-PM.png) **Status** - A short status update, similar to a Twitter status update. [![Post Format Status](http://make.wordpress.org/training/files/2014/10/status-1024x285.png)](http://make.wordpress.org/training/files/2014/10/status.png)   **Video** - A single video or video playlist. The first <video /> tag or object/embed in the post content could be considered the video. Alternatively, if the post consists only of a URL, that will be the video URL. May also contain the video as an attachment to the post, if video support is enabled on the blog (like via a plugin). [![Video Post Formats](http://make.wordpress.org/training/files/2014/08/Screen-Shot-2014-08-01-at-2.30.07-PM-1024x627.png)](http://make.wordpress.org/training/files/2014/08/Screen-Shot-2014-08-01-at-2.30.07-PM.png) **Audio** - An audio file or audio playlist. Could be used for Podcasting. [![Audio Post Formats](http://make.wordpress.org/training/files/2014/08/Screen-Shot-2014-08-01-at-2.34.35-PM-1024x403.png)](http://make.wordpress.org/training/files/2014/08/Screen-Shot-2014-08-01-at-2.34.35-PM.png) **Chat** - A chat transcript, like so: [![Chat Post Formats](http://make.wordpress.org/training/files/2014/08/Screen-Shot-2014-08-01-at-2.16.34-PM-1024x465.png)](http://make.wordpress.org/training/files/2014/08/Screen-Shot-2014-08-01-at-2.16.34-PM.png)

### Why Use Post Formats?

Using Post Formats, your blog visitors will know exactly what type of content they are viewing.  Different styles for each Post Format will make your blog more visually interesting. Previously, developers tried to accomplish these unique styles for content by modifying categories or by using custom post types.  These custom types were intended to be something other than blog content. Using Post Formats will keep your content all within the blog portion of your site, and once configured, will require only that you check which format you are using. Post Formats will show up in your RSS feed, and will be editable within the Posts part of your site.

### How Post Formats Work

When you edit an individual post, you’ll see a **Format** module: [![post formats checkbox](http://make.wordpress.org/training/files/2014/10/post-format.png)](http://make.wordpress.org/training/files/2014/10/post-format.png)   [tip]If you do not see the **Format** module, check that you have it enabled in your [Screen Options](http://codex.wordpress.org/Posts_Screen#Screen_Options "Screen Options"). If you don’t see the **Format** option there, then you are likely using a theme that does not use post formats.[/tip] Once you've assigned posts to a particular Post Format, you will see icons in the dashboard indicating which format each post is.  Go to Posts > All Posts: [![Post Formats in Dashboard](http://make.wordpress.org/training/files/2014/10/edit-post-formats.png)](http://make.wordpress.org/training/files/2014/10/edit-post-formats.png) When viewing your blog, the content will have a unique look for each format. [![Post Formats Example](http://make.wordpress.org/training/files/2014/10/postformatsexample.png)](http://make.wordpress.org/training/files/2014/10/postformatsexample.png)

## <span class="mw-headline">Adding Theme Support</span>

Themes need to use <tt>[add_theme_support()](http://codex.wordpress.org/Function_Reference/add_theme_support "Function Reference/add theme support")</tt> in the _functions.php_ file to tell WordPress which post formats to support by passing an array of formats like so:

<pre>add_theme_support( 'post-formats', array( 'aside', 'quote', 'status', 'image', 'gallery', 'chat', 'link', 'audio', 'video' ) );
</pre>

  [info] that you must call this before the [init](http://codex.wordpress.org/Plugin_API/Action_Reference/init "Plugin API/Action Reference/init") hook gets called! A good hook to use is the [after_setup_theme](http://codex.wordpress.org/Plugin_API/Action_Reference/after_setup_theme "Plugin API/Action Reference/after setup theme") hook.[/info]

## <span class="mw-headline">Adding Post Type Support</span>

If you would like to use Post Formats styling on Pages or Custom Post Types, it is possible. Post Types need to use <tt>[add_post_type_support()](http://codex.wordpress.org/Function_Reference/add_post_type_support "Function Reference/add post type support")</tt> in the _functions.php_ file to tell WordPress which post formats to support:

<pre>// add post-formats to post_type 'page'
add_post_type_support( 'page', 'post-formats' );

// add post-formats to post_type 'my_custom_post_type'
add_post_type_support( 'my_custom_post_type', 'post-formats' );</pre>

## Using Post Formats

In the theme, make use of <tt>[get_post_format()](http://codex.wordpress.org/Function_Reference/get_post_format "Function Reference/get post format")</tt> to check the format for a post, and change its presentation accordingly. Note that posts with the default format will return a value of FALSE. Or make use of the <tt>[has_post_format()](http://codex.wordpress.org/Function_Reference/has_post_format "Function Reference/has post format")</tt> [conditional tag](http://codex.wordpress.org/Conditional_Tags "Conditional Tags"):

<pre>if ( has_post_format( 'video' )) {
  echo 'this is the video format';
}
</pre>

An alternate way to use formats is through styling rules. Themes should use the <tt>[post_class()](http://codex.wordpress.org/Template_Tags/post_class "Template Tags/post class")</tt> function in the wrapper code that surrounds the post to add dynamic styling classes. Post formats will cause extra classes to be added in this manner, using the "format-foo" name. For example, one could hide post titles from status format posts by putting this in your theme's stylesheet:

<pre>.format-status .post-title {
display:none;
}</pre>

### Styling Post Formats

Although you can style and design your formats to be displayed any way you see fit, each of the formats lends itself to a certain type of "style", as dictated by modern usage. It is well to keep in mind the intended usage for each format, as this will lend them towards being easily recognized as a specific type of thing visually by readers. For example, the aside, link, and status formats will typically be displayed without title or author information. They are simple, short, and minor. The aside could contain perhaps a paragraph or two, while the link would probably be only a sentence with a link to some URL in it. Both the link and aside might have a link to the single post page (using <tt>[the_permalink()](http://codex.wordpress.org/Function_Reference/the_permalink "Function Reference/the permalink")</tt>) and would thus allow comments, but the status format very likely would not have such a link. An image post, on the other hand, would typically just contain a single image, with or without a caption/text to go along with it. An audio/video post would be the same but with audio/video added in. Any of these three could use either plugins or standard [Embeds](http://codex.wordpress.org/Embeds "Embeds") to display their content. Titles and authorship might not be displayed for them either, as the content could be self-explanatory. The quote format is especially well suited to posting a simple quote from a person with no extra information. If you were to put the quote into the post content alone, and put the quoted person's name into the title of the post, then you could style the post so as to display <tt>[the_content()](http://codex.wordpress.org/Function_Reference/the_content "Function Reference/the content")</tt> by itself but restyled into a [blockquote](http://codex.wordpress.org/User:Lorelle/Customizing_The_Content#Blockquotes "Blockquote") format, and use <tt>[the_title()](http://codex.wordpress.org/Function_Reference/the_title "Function Reference/the title")</tt> to display the quoted person's name as the byline. A chat in particular will probably tend towards a monospaced type display, in many cases. With some styling on the .format-chat, you can make it display the content of the post using a monospaced font, perhaps inside a gray background div or similar, thus distinguishing it visually as a chat session. See [Post Formats: Chat](http://justintadlock.com/archives/2012/08/21/post-formats-chat "Post Formats: Chat") for further styling.

### <span id="Formats_in_a_Child_Theme" class="mw-headline">Formats in a Child Theme</span>

[Child Themes](http://codex.wordpress.org/Child_Themes "Child Themes") inherit the post formats defined by the parent theme. Calling <tt>[add_theme_support()](http://codex.wordpress.org/Function_Reference/add_theme_support "Function Reference/add theme support")</tt> for post formats in a child theme must be done at a later priority than that of the parent theme and will **override** the existing list, not add to it.

<pre>add_action( 'after_setup_theme', 'childtheme_formats', 11 );
function childtheme_formats(){
     add_theme_support( 'post-formats', array('aside', 'quote', 'status', 'image', 'gallery', 'chat', 'link', 'audio', 'video') ); }</pre>

Calling <tt>[remove_theme_support('post-formats')](http://codex.wordpress.org/Function_Reference/remove_theme_support "Function Reference/remove theme support")</tt> will remove it all together.

## Group Exercises

1.  Using Twenty Thirteen theme, create a post using each post format option.
2.  Using Underscores:
    1.  Create each Post Format [info]Model after [Twenty Thirteen theme files](https://github.com/WordPress/WordPress/tree/master/wp-content/themes/twentythirteen "Twenty Thirteen") but remember to change calls to the theme naming convention to your own theme[/info]
        1.  [content-aside.php](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentythirteen/content-aside.php "Content-Aside.php")
        2.  [content-audio.php](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentythirteen/content-audio.php "Content-Audio.php")
        3.  [content-chat.php](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentythirteen/content-chat.php "Content-Chat.php")
        4.  [content-gallery.php](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentythirteen/content-gallery.php "Content-Gallery.php")
        5.  [content-image.php](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentythirteen/content-image.php "Content-Image.php")
        6.  [content-link.php](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentythirteen/content-link.php "Content-Link.php")
        7.  [content-quote.php](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentythirteen/content-quote.php "Content-Quote.php")
        8.  [content-status.php](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentythirteen/content-status.php "Content-Status.php")
        9.  [content-video.php](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentythirteen/content-video.php "content-video.php")
        10.  [content-none.php](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentythirteen/content-none.php "Content-None.php")
    2.  Style Post Formats (model after Twenty Thirteen [Style.css](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentythirteen/style.css#L1380 "Style.css") line 1380)

## Quiz

1.  What are Post Formats? _Post Formats are used by a theme to customize its presentation of a post. The Post Formats feature provides a standardized list of formats that are available to all themes that support the feature._
2.  What are several Post Format options? _Aside, audio, chat, gallery, image, link, quote, status, video_
3.  Are Post Formats the same as Custom Post Types? When would you pick a Custom Post Type instead of a Post Format? _No, custom post types appear as another option on the admin dashboard near posts and pages.  Custom Post Types are useful when you don't want the content to appear on /blog, such as an events calendar or real estate listings._
4.  Where do you enable Post Formats for your theme? _Functions.php, specifically in a child theme functions.php_
5.  What must you do when writing a post that should use a Post Format? _Select which post format to use_
6.  Where do you customize the look for Post Formats? _Style.css, or specifically the child theme style.css_
7.  Do all themes support Post Formats? _No_
8.  What default WordPress themes support Post Formats? _Twenty Thirteen and Twenty Fifteen_
9.  Can you add Post Format support to your theme or child theme? _Yes_
