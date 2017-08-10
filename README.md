## Welcome to breakingstuff's page containing jobfinder.dk rss feed reader.

```php
<?php
   $rss = new DOMDocument();
   $rss->load('https://www.jobfinder.dk/jobsrss/');
   $feed = array();
   foreach ($rss->getElementsByTagName('item') as $node) {
      $item = array(
                'title' => $node->getElementsByTagName('title')->item(0)->nodeValue,
                'desc' => $node->getElementsByTagName('description')->item(0)->nodeValue,
                'link' => $node->getElementsByTagName('link')->item(0)->nodeValue,
                );
      array_push($feed, $item);
   }
   $limit = 60;
   for($x=0;$x<$limit;$x++) {
      $title = str_replace(' & ', '&amp; ', $feed[$x]['title']);
      $link = $feed[$x]['link'];
      $description = $feed[$x]['desc'];
      echo '<p><b><a href="'.$link.'" target="_blank">'.$title.'</a></b></p>';
      echo '<p>'.$description.'</p>';
   }
?>
```
The PHP script creates a $rss variable that calls a new DOMDocument() and then uses the loads() function to define the url to the job site. $feed variable then creates and array() function passed to a $item variable containing the DOM objects to read: title, description, link. 

Then pushes the $feed variable into $item merging the array() function with the defined values. We then set a limit of max 60 entries and do a for() function where we define variable $x and append as long as $x is lower value than $limit variable. 

Now we define the variable $title using str_replace() to remove make the output much more clean. $link variable defines the link to the job posting. $description variable contains a short description about the job position. Now we echo the output in two lines, merging the $title and $link variables so the title acts as a link. 

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/breakingstuff/jobfinder.dk-rss-reader/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
