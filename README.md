Kurenai
==============

[![Join the chat at https://gitter.im/orchestral/platform/components](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/orchestral/platform/components?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Kurenai is a Markdown document parser which allows for extra metadata to be associated with the document.

[![Latest Stable Version](https://img.shields.io/github/release/orchestral/kurenai.svg?style=flat-square)](https://packagist.org/packages/orchestra/kurenai)
[![Total Downloads](https://img.shields.io/packagist/dt/orchestra/kurenai.svg?style=flat-square)](https://packagist.org/packages/orchestra/kurenai)
[![MIT License](https://img.shields.io/packagist/l/orchestra/kurenai.svg?style=flat-square)](https://packagist.org/packages/orchestra/kurenai)
[![Build Status](https://img.shields.io/travis/orchestral/kurenai/master.svg?style=flat-square)](https://travis-ci.org/orchestral/kurenai)
[![Coverage Status](https://img.shields.io/coveralls/orchestral/kurenai/master.svg?style=flat-square)](https://coveralls.io/r/orchestral/kurenai?branch=master)
[![Scrutinizer Quality Score](https://img.shields.io/scrutinizer/g/orchestral/kurenai/master.svg?style=flat-square)](https://scrutinizer-ci.com/g/orchestral/kurenai/)

## Introduction

Confused? Let's take a look at how it works.

This is what your documents might look like:

    title: This is my document title.
    slug: this-is-the-slug
    date: 12th December 1984
    -------
    This is my **markdown** content!

and here is how you will parse it with Kurenai :

```php
<?php

// Use the Kurenai document parser.
use Kurenai\Document;
use Kurenai\DocumentParser;
use Kurenai\Parser\Parsedown;

// Load our document source.
$source = file_get_contents('my_document.md');

// Create a new document parser
$parser = new DocumentParser(new Document(new Parsedown));

// Parse the loaded source.
$document = $parser->parse($source);

// To get the document content in raw markdown format..
// This is my **markdown** content!
$rawMarkdown = $document->getContent();

// To get the converted HTML content..
// <p>This is my <strong>markdown</strong> content!</p>
$html = $document->getHtmlContent();

// To access the full array of metadata
// array(
//      'title'     => 'This is my document title.',
//      'slug'      => 'this-is-the-slug',
//      'date'      => '12th December 1984'
// );
$metadata = $document->get();

// To access a piece of metadata by key (default: null)..
// this-is-the-slug
$slug = $document->get('slug');
```

## Origin

Kurenai is a forked project from [daylerees/kurenai](https://github.com/daylerees/kurenai).
