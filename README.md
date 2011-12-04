# [YooTheme Zoo - SEO Title Tags](http://github.com/aaronbrownell/yootheme-zoo-seo-title-tags)


This hack allows text inside the title tag `<title>` to be different from the main page heading text inside the `<h1>`:

	<!doctype html>
	<html>
	<head>
		<title>Custom Title Tag Text for Search Engines</title>
	</head>
	<body>
		<h1>Can Be Different then Page Title</h1>
	</body>
	</html> 

## How To Install

Note: Works with Zoo 2.4.11. View commit history additions to modify other versions of 2.0-2.4. Zoo 2.5+ has native title tag support in the Admin and does not need this workaround.

1. Replace the two files below with the two files in download:

	>	`/components/com_zoo/controllers/default.php`  

	>	`/media/zoo/applications/blog/templates/default/renderer/item/positions.xml`

2. In the Joomla Admin:
  
	>	a. Navigate to Components->ZOO  
	>	b. Click the tab with the Gear icon.  
	>	c. From the App Manager click on an App to configure it (Blog for example).  
	>	d. Hover over the Instance of the App Name you gave the Blog Type (Article for example) and click "Edit Elements".  
	>	e. Create a custom text field called 'Browser Title' and Save. This will hold the custom title tag text.


3. On line 165 `default.php`:
        
		165. if ($this->item->application_id == 1 && $this->item->type == "article") {  

	>	a. Replace the number `1` with your id number.  
	>	b. Replace `article` with the name you gave your Zoo App instance in the Joomla Admin.  
	>	c. Steps a & b can be found in MySQL table `zoo_application`.

4. On line 179 of `default.php`:

		179. $title = getZooElementData($this->item->id, 'f89d78b8-daa7-4983-be3b-1bd83a29ce5c', 'value');

	>	a. Replace `f89d78b8-daa7-4983-be3b-1bd83a29ce5c` with your Custom Field ID for 'Browser Title'. Your Custom ID is located in MySQL table `jos_zoo_item` under `elements`.
		 

## Resources

* [Joomla](http://joomla.com/): GNU/GPLv2
* [YooTheme Zoo](http://yootheme.com/zoo/): GNU/GPLv2
* Paul Mason [Yootheme Zoo - Accessing Element Data with Joomla Code](http://paulmason.name/blog/item/yootheme-zoo-accessing-element-data-with-joomla-code)
