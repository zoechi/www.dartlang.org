---
layout: default
title: "pub publish"
description: "Use pub publish to publish your Dart package to pub.dartlang.org."
---

{% include breadcrumbs.html %}

# {{ page.title }}

_Publish_ is one of the commands of the _pub_ tool.
[Learn more about pub](/tools/pub/).

{% prettify sh %}
$ pub publish [--dry-run] [--force] [--server <url>]
{% endprettify %}

This command publishes your package on
[pub.dartlang.org](http://pub.dartlang.org) for anyone to download and depend
on. For information on how to prepare your package for publishing,
and what files you should include or exclude,
see [Publishing a Package](../publishing.html).

## Options

For options that apply to all pub commands, see
[Global options](/tools/pub/cmd/#global-options).

### `--dry-run` or `-n`

With this, pub goes through the validation process but does not actually upload
the package. This is useful if you want to see if your package meets all of the
publishing requirements before you're ready to actually go public.

### `--force` or `-f`

With this, pub does not ask for confirmation before publishing. Normally, it
shows you the package contents and asks for you to confirm the upload.

If your package has errors, pub doesn't upload it and exits with an error.
In the event of warnings, your package *is* uploaded.
To ensure that your package has no warnings before uploading,
either don't use `--force`, or use `--dry-run` first.

### `--server`

If you pass `--server` followed by a URL, it attempts to publish the
package to that server. It assumes the server supports the same HTTP API that
[pub.dartlang.org][pubsite] uses.

This can be useful if you're running your own local package server for testing.
The main pub server is itself open source and available [here][pub repo].

[pubsite]: http://pub.dartlang.org
[pub repo]: https://github.com/dart-lang/pub-dartlang

<aside class="alert alert-info" markdown="1">
*Problems?*
See [Troubleshooting Pub](../troubleshoot.html).
</aside>

