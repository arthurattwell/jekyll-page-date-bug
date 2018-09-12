---
---

This minimal Jekyll site shows on my systems[^1] that:

- when running `jekyll serve` without `--incremental`, pages in collections do not get a `page.date`;
- but when running `jekyll serve --incremental`, pages in collections do get the build timestamp as their `page.date`. That timestamp is the time of the last time the page built.

See [this collection page](test) to test whether a `page.date` is assigned in the current build.

For instance:

1. Build the site with `jekyll serve` at 12:00. The `page.date` does not generate on the collection page.
2. Stop the server.
3. Build the site with `jekyll serve --incremental` at 12:01. The `page.date` *does* appear on the collection page as 12:00.

    So the `--incremental` build does rebuild the collection page, but using the previous build's timestamp.

4. With the incremental build still running, save the collection-page's markdown file to trigger a rebuild of that page only. Say this is at 12:02.
5. The collection page now *does* include the generated `page.date` with a new timestamp of 12:02.

This applies when the collection page does *not* include a `date:` in its YAML page frontmatter. When page frontmatter includes a `date:`, the `page.date` always generates as expected.

Note that pages outside collections (like this home page) never get an automatic `page.date`. For instance, no `page.date` here: {{ page.date }}. This may be expected behaviour but is not the subject of this test.

[^1]: Windows 10 Pro with Ruby 2.3.3 and Jekyll 3.8.3; Ubuntu 16.04 with Ruby 2.4.1 and Jekyll 3.8.3.
