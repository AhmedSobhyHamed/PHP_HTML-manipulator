# PHP_HTML-manipulator

Read HTML with a variable pattern to create a dynamic website using the PHP scripting language.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Errors](#Errors)
- [Technologies Used](#technologies-used)
- [License](#license)
- [Contact](#contact)

  <!-- intro -->

## Introduction

This library is used to place your fetched data directly into an HTML page, making it easy to create dynamic web pages and change the content of any HTML page before rendering it.

#### who find it useful.

Anyone who creates small and medium projects and wants a tool to easily edit HTML files without using frameworks.

#### what you can do.

- Add the fetched data from, let's say, the database into an HTML file and replace a pattern with a single value at a time.
- Replace a pattern with an array of data to iterate through a snippet of code. For example, the `li` element in lists or the `td` element in tables.

  <!-- technologies was used with links if available -->

## Features

```diff
- Suitable for small/medium projects.
- Used without any framwork.
- Used with vanilla PHP.
- Easy to use.
- Easy change content of html template with php.
- Set custom delimiter you want to replace.
```

  <!-- get start and how to run with the prerequisites mintion -->

## Installation

1. Clone the repository:

   ```sh
   git clone https://github.com/AhmedSobhyHamed/PHP_HTML-manipulator.git
   ```

2. copy to the project directory:

   ```sh
   cp HTML_HANDLER.php <project_dir>/<name>.php
   ```

  <!-- usage or how to interact with this technologies like api end points and what they do -->

## Usage

#### include the file

in the top of the page include the library.
<br>
like:

```php
require_once 'HTML_HANDLER.php';
```

#### intialize

Create an instance and pass to the constructor arguments that represent the start and end tags that identify the pattern. Alternatively, don't pass any arguments, and the default pattern tag will be used.

```diff
+ the difault tag loks like: <#{{ VariableName }}#>
```

example :

```php
$page = new HTML_TEMPLATE(); // the default <#{{ var }}#> will used
// or
$page = new HTML_TEMPLATE('{{','}}'); // {{ var }} will used
```

Then call the file that contains HTML with pattern tags that need to be replaced.

```php
$page->get_file('dir/index.html');
```

#### adding data.

There are two ways to add data. the first is to add a single value, and the second is to add an array or multiple values.

##### adding a single value.

first create the pattern in HTML file like:

```html
<p>text no need to be replaced.</p>
<p>{{ title }}</p>
<!-- or -->
<p><#{{ title}}#></p>
<p>text no need to be replaced.</p>
```

and feel free to use whitespaces.
<br>
then in php file use:

```php
$page->add_data('title','hello');
//or
$page->add_data('title',$database->value);
```

##### adding multi values.

first create the pattern in HTML file like:

```html
<p>text no need to be replaced.</p>
<ul>
  <{{LOOP (items as item)}}>
  <li><{{item->key1}}></li>
  <li><{{item->key2}}></li>
  ... <{{LOOP_END}}>
</ul>
<p>text no need to be replaced.</p>
```

and feel free to use whitespaces.
<br>
then in php file use:

```php
$page->add_data('items',[
   ['key1'=>'val','key2'=>'val',...],
   ['key1'=>'val','key2'=>'val',...],
   ...
   ]);
```

#### ready to render.

now after replace every thing you can get a string that populated with HTML code after editd.

```php
echo $page->get_page();
//or
$string = $page->get_page();
```

```diff
! warning: this function will return false is there is no file opened.
```

## Errors

This library uses a try-catch block architecture and throws exceptions that include messages:
<br>
<code style="green">FNF</code>
That happens when the file you pass does not exist or when you forget to pass it at all.
<br>
<code style="green">NFO</code>
That happens when the file is accessed or used at that moment in a way that locks any other reading attempts.

## Technologies Used

- languages:

  - PHP

## License

This project is licensed under the MIT License - see the [LICENSE](/LICENSE) file for details

  <!-- contacts -->

## Contact

Created by [Ahmed Sobhy]:

- email: [ahmed.s.abdulaal@gmail.com](mailto:ahmed.s.abdulaal@gmail.com)
- linkedin: [Ahmed Sobhy](https://www.linkedin.com/in/ahmed-sobhy-b824b7201/)
  <br>
  feel free to contact me!
