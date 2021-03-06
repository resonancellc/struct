# Struct

[![Software License][ico-license]](LICENSE.txt)
[![Build Status][ico-travis]][link-travis]
[![codecov][ico-codecov]][link-codecov]
[![Codacy Badge][ico-codacy]][link-codacy]

Implementation of composite type for PHP.

Contains methods to create from associated array, JSON string or another Struct, with/without type cast.

## Requirements

*   PHP >= 7.1

## Install

Install with [Composer](http://getcomposer.org):
    
```bash
composer require php-strict/struct
```

## Usage

Define your own composite type by extending Struct class:

```php
use PhpStrict\Struct\Struct

class Book extends Struct
{
    /**
     * @var string
     */
    public $author = '';
    
    /**
     * @var string
     */
    public $title = '';
    
    /**
     * @var string
     */
    public $isbn = '';
    
    /**
     * @var int
     */
    public $pages = 0;
    
    /**
     * @var bool
     */
    public $publicated = false;
    
    /**
     * @var array
     */
    public $tags = [];
}
```

Now you can fill your strcuture with data:

```php
//book with classic assign data to class fields
$book1 = new Book();
$book1->author = 'Author Name';
$book1->title = 'Book title 1';
$book1->isbn = '000-0-000-00000-0';
$book1->pages = 240;
$book1->publicated = true;
$book1->tags = ['fantastic', 'space', 'detective'];

//another book with data through array
$book2 = new Book([
    'author' => 'Author Name',
    'title' => 'Book title 2',
    'isbn' => '000-0-000-00000-0',
    'pages' => 156,
    'publicated' => true,
    'tags' => ['drama', 'nature'],
]);

//another book with data through JSON
$json = '{"author":"Author Name","title":"Book title 3","isbn":"000-0-000-00000-0","pages":156,"publicated":true,"tags":["comedy","city"]}';
$book3 = new Book($json);

//book, based on existing book
$book4 = new Book($book1);
$book4->title = 'Book title 4';
```

See examples dir.

## Tests

To execute the test suite, you'll need [Codeception](https://codeception.com/).

```bash
vendor\bin\codecept run
```

[ico-license]: https://img.shields.io/badge/license-GPL-brightgreen.svg?style=flat-square
[ico-travis]: https://img.shields.io/travis/php-strict/struct/master.svg?style=flat-square
[link-travis]: https://travis-ci.org/php-strict/struct
[ico-codacy]: https://api.codacy.com/project/badge/Grade/92ff05432c1c4c1b8599e1f53ee5c15a
[link-codacy]: https://www.codacy.com/app/php-strict/struct?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=php-strict/struct&amp;utm_campaign=Badge_Grade
[ico-codecov]: https://codecov.io/gh/php-strict/struct/branch/master/graph/badge.svg
[link-codecov]: https://codecov.io/gh/php-strict/struct
