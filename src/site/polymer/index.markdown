---
layout: default
title: "Polymer.dart"
description: "Standards-based web components:
custom elements, templates,
and data binding for Dart web apps. A Dart port of Polymer."
has-permalinks: true
---

{% include toc.html %}

<h1>
  {{page.title}}
  <img src="images/polymer-logo.svg" alt="Polymer logo"
       style="vertical-align:baseline" height="35">
</h1>

Use polymer.dart—a Dart port of [Polymer](http://www.polymer-project.org)—to
build structured, encapsulated, client-side web apps with Dart and
web components.

![Paper sampler on mobile](images/iconbutton-small.png)
![Paper sampler on desktop](images/iconbutton-big.png){: .thinborder}

With polymer.dart, you can:

* Use Polymer custom elements.
* Design your own HTML tags to encapsulate style, structure, and behavior.
* Create live, two-way bindings between Dart objects and DOM nodes.
* Use emerging web standards—Custom Elements, HTML Imports, Shadow DOM,
  and more—today.

{% comment %}
PENDING: Talk about advantages of polymer.dart development process
(why you should use it instead of polymer.js).
{% endcomment %}

<aside class="alert alert-info" markdown="1">
**Note:**
The code samples on this page reflect **polymer.dart 0.16**.
{% comment %}
UPDATE version each release
{% endcomment %}
For information about polymer.dart versions, see the
[Release Notes](/polymer/reference/release-notes/).
</aside>


<hr>
## Where to start {#start}

You can get a quick start with any of the following:

[Polymer Dart Code Lab](/codelabs/polymer/)
: Follow this if you like to learn by coding.
This code lab walks you through building a single-page admin console and
the custom elements that it requires.

[Tutorial: Define a Custom Element](/docs/tutorials/polymer-intro/)
: Read this if you like a more structured walkthrough.
This tutorial provides a detailed introduction to using polymer.dart
to create custom elements.

[Frequently Asked Questions (FAQ)](faq.html)
: Get the answers to common questions about polymer.dart.
This page has up-to-the-minute information that
hasn't yet made its way into the documentation.

Still here? Keep reading!


<hr>
## Structuring your app

Apps that use polymer.dart follow the
[pub package layout conventions](/tools/pub/package-layout.html).
As a consequence, the source code for a polymer.dart app
starts with a top directory containing a
`pubspec.yaml` file and a `web` directory:

![app/pubspec.yaml, app/web/index.html](images/dir-simplest-structure.png)

The `web` directory contains HTML files that are
_entry points_—pages that users can visit.
Other files (Dart files, CSS, images, and so on)
can also be in the `web` directory.

The `pubspec.yaml` file has metadata about the app,
such as the pub packages that it depends on.

Learn more at
[Imports and Your App's Directory Structure](app-directories.html).

<hr>
## Installing polymer.dart

Get polymer.dart from pub.dartlang.org,
the Dart package hosting service.

Edit your `pubspec.yaml` file
to depend on the `polymer` package and
use the `polymer` transformer:

{% prettify yaml %}
dependencies:
  polymer: ">=0.15.1 <0.17.0"
transformers:
- polymer
{% endprettify %}
{% comment %}
UPDATE version each release
{% endcomment %}

Then, run `pub get` to download the package and link it into your app.


<hr>
## Using custom elements

Here's an example of some HTML code
that uses a `<paper-input>` element
from the paper_elements package:

<!-- from polymer/get_element/web/index.html -->
{% prettify html %}
<head>
  ...
  <link rel="import" href="[[highlight]]packages/paper_elements/paper_input.html[[/highlight]]">
  ...
</head>
<body unresolved>
  [[highlight]]<paper-input label="Type something..."></paper-input>[[/highlight]]
  ...
  <script type="application/dart">export 'package:polymer/init.dart';</script>
</body>
{% endprettify %}

For more information, see [Using Elements](using-elements/).


<hr>
## Creating custom elements

You can extend the lexicon of HTML with your own custom elements,
as described in
[Creating Elements](creating-elements/).


<hr>
## Tools

Polymer.dart works well with Dart tools, such as Dart Editor and Pub.

### Generating warnings

Polymer.dart offers a linter that reports syntax or usage warnings.
Using a special `build.dart` file,
you can connect the linter to Dart Editor to display warnings directly
at the source.

Create a `build.dart` file at the root of your project,
and put the following code in it:

{% prettify dart %}
export 'package:polymer/default_build.dart';
{% endprettify %}

Dart Editor runs `build.dart` after a file is saved, and
displays warnings from the linter.

Learn more about [Dart Editor](/tools/editor/).

![Polymer warning in Dart Editor](images/lint-warning.png)


### Building

Use `pub build` to compile your polymer.dart app into JavaScript so that
it can run across the modern web. The build process also concatenates files
for faster loading.

You can use `entry_points` to specify which pages under `web`
the user can navigate to.
(By default, all pages under `web` are entry points.)
For example:

{% prettify yaml %}
transformers:
- polymer:
    entry_points: web/index.html
{% endprettify %}

Run `pub build` from the root of your project to generate a `build`
directory.

{% prettify bash %}
> pub build
{% endprettify %}

The `build` directory contains the HTML, JavaScript, and other assets
required to run the application. You can then deploy the `build` directory
to your favorite web server.

Learn more about [pub build](/tools/pub/cmd/pub-build.html).


<hr>

## Source code

You can view sample source code that _uses_ polymer.dart,
as well as the source code that _implements_ polymer.dart.


### Samples

Here are a few places to find polymer.dart sample code:

{% comment %}
{PENDING: introduce. point to more ways to find samples/source code.}
{% endcomment %}

[polymer-dart-patterns](https://github.com/dart-lang/polymer-dart-patterns)
: Small, useful samples that show how to do things the polymer.dart way.

[polymer-spa-example](https://github.com/dart-lang/polymer-spa-example)
: A simple example of a full polymer app with multiple pages.
  Learn more about the example at [Building Single Page Apps using
  Polymer.dart](/polymer/spa/).

[polymer-and-dart-codelab](https://github.com/dart-lang/polymer-and-dart-codelab)
: A larger sample, implementing the app featured in
[Polymer Dart Code Lab](/codelabs/polymer/).


### Polymer.dart

Polymer.dart is open source. You can view and contribute to the source of
polymer.dart and its many component packages on github.

  * [Polymer.dart](https://github.com/dart-lang/polymer-dart)
  * [Template Binding](https://github.com/dart-lang/template-binding)
  * [Polymer Expressions](https://github.com/dart-lang/polymer-expressions)
  * [Web Components](https://github.com/dart-lang/web-components)
  * [Observe](https://github.com/dart-lang/observe)
  * [Core Elements](https://github.com/dart-lang/core-elements)
  * [Paper Elements](https://github.com/dart-lang/paper-elements)

<hr>

## Support and more

We actively encourage your feedback and questions.

* Ask your [how-to questions][so] on StackOverflow.
* Join the [general discussion about polymer.dart][web-list] on our mailing
  list.
* Send [feedback on the web components family of specifications][polymer-dev-list]
  to the polymer-dev mailing list.
  (Note: That list isn't Dart specific.)
* Please file [bugs and feature requests][new-issue] for polymer.dart.

[so]: http://stackoverflow.com/tags/dart
[web-list]: https://groups.google.com/a/dartlang.org/forum/#!forum/web
[polymer-dev-list]: https://groups.google.com/forum/?fromgroups=#!forum/polymer-dev
[new-issue]: https://github.com/dart-lang/polymer-dart/issues/new

Keep an eye on this page and the [FAQ](faq.html)
for the latest information about polymer.dart.
