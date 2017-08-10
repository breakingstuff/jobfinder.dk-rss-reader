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

Now we define the variable $title using str_replace() to remove start of a character reference and ampersand to make the output much more clean. $link variable defines the link to the job posting. $description variable contains a short description about the job position. Now we echo the output in two lines, merging the $title and $link variables so the title acts as a link. 

### Bootstrap added

```html
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-alpha.6/css/bootstrap.min.css" integrity="sha384-rwoIResjU2yc3z8GV/NPeZWAv56rSmLldC3R/AZzGRnGxQQKnKkoFVhFQhNUwEyJ" crossorigin="anonymous">
<script src="https://code.jquery.com/jquery-3.1.1.slim.min.js" integrity="sha384-A7FZj7v+d/sdmMqp/nOQwliLvUsJfDHW+k9Omg/a/EheAdgtzNs3hpfag6Ed950n" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/tether/1.4.0/js/tether.min.js" integrity="sha384-DztdAPBWPRXSA/3eYEEUWrWCy7G5KFbe8fFjk5JAIxUYHKkDx6Qin1DkWx51bBrb" crossorigin="anonymous"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-alpha.6/js/bootstrap.min.js" integrity="sha384-vBWWzlZJ8ea9aCX4pEW3rVHjgjt7zpkNpZk+02D9phzyeVkE+jo0ieGizqPLForn" crossorigin="anonymous"></script>
```
By using Bootstrap CDN we make the output much cleaner. Include the lines in your header section.
To make it centered output use the ```html <div class="container">(PHP CODE GOES HERE)</div>```

# Full Code
```php
<html>
<head>
<title>Ledige Stillinger</title>

<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-alpha.6/css/bootstrap.min.css" integrity="sha384-rwoIResjU2yc3z8GV/NPeZWAv56rSmLldC3R/AZzGRnGxQQKnKkoFVhFQhNUwEyJ" crossorigin="anonymous">
<script src="https://code.jquery.com/jquery-3.1.1.slim.min.js" integrity="sha384-A7FZj7v+d/sdmMqp/nOQwliLvUsJfDHW+k9Omg/a/EheAdgtzNs3hpfag6Ed950n" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/tether/1.4.0/js/tether.min.js" integrity="sha384-DztdAPBWPRXSA/3eYEEUWrWCy7G5KFbe8fFjk5JAIxUYHKkDx6Qin1DkWx51bBrb" crossorigin="anonymous"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-alpha.6/js/bootstrap.min.js" integrity="sha384-vBWWzlZJ8ea9aCX4pEW3rVHjgjt7zpkNpZk+02D9phzyeVkE+jo0ieGizqPLForn" crossorigin="anonymous"></script>
</head>
<body>
<div class="container">

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
</div>
</body>
</html>
```
