# picStylizer

picStylizer is a PHP class that create sprite and css style file from images folder

Notice: if you want to change the image onMouseOver (hover) you have add "_hover" at the end of filename before the extention. Example: 
```
// initial image
icon.png
// hover image
icon_hover.png

// the result css code will be:
.icon {...}
.icon:hover {...}
```

# Usage

```php
include("./picStylizer.php");

// Initialize Class
$pS = new picStylizer();

// define folder configuration
$config = array(
	// set the origin folder
	"origin" => array(
		"images" => "origin/images" // folder from where the script will take the images,
		"include_subfolders" => true
	),
	// set destination folder
	"destination" => array(
		"styles" => "destination/css/sprites.css", // define css style of sprites
		"sprites" => "destination/sprites/sprites.png", // define the sprite image result
		//"example" => "destination/example/sprites.html", // define the html example
		"rel_path_to_sprite_image" => "./", // define the path
		"rel_path_to_sprite_css" => "./"    // define the path
	)
);
$pS->setFoldersConfig($config);

// resize images
$pS->resizeCoefficient(0.7);

// define minization (default: true)
$pS->setMinization();

// define css style by default
$pS->setCssInit($css ='body {backgound-color:#000; color:#fff; font-size:14px;}', $class_prefix='mySprite');

// gen sprites, styles and html example
set_time_limit(1000);
$pS->getSprite($save_html=true, $redirect_to_html=true);
```


# Results
Output source code will be like this:

```
<div class="sprite-each mySprite-image1"></div>
<div class="sprite-each mySprite-image2"></div>
<link rel="stylesheet" href="./sprites.css">
					↓
				body {background-color:#000;font-family:courier;color:#fff;font-size:14px;}
				.sprite-each{background-image:url("./sprites.png"); 
				.mySprite-image1 {background-position: 0 -XXX; background-repeat:no-repeat;width:XXX; height:XXX}
				.mySprite-image2 {background-position: 0 -XXX; background-repeat:no-repeat;width:XXX; height:XXX}
...
``` 
