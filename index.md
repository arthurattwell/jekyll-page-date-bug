---
---

This minimal Jekyll site shows on my systems[^1] that:

- when running `jekyll serve` without `--incremental`, pages in collections do not get a `page.date`;
- but when running `jekyll serve --incremental`, pages in collections do get the build timestamp as their `page.date`

when those pages do not include a `date:` in their YAML page frontmatter.

Pages outside collections like this one do not get a `page.date`. For instance, no `page.date` here: {{ page.date }}

See [this collection page](test) to test whether a `page.date` is assigned.

[^1]: Windows 10 Pro with Ruby 2.3.3 and Jekyll 3.8.3; Ubuntu 16.04 with Ruby 2.4.1 and Jekyll 3.8.3.
