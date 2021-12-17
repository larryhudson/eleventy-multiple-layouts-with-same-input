# Troubleshooting: generating multiple output files from a single input

I'm trying to find a way to find a way to render multiple templates using the same content.

For example, using a single Markdown file and generating multiple versions using two different templates.

I'm trying to do this so that I can render a 'print-friendly' version of a page, alongside a standard version.

In this repo, I have tried making a [collection](https://www.11ty.dev/docs/collections/) and using [pagination](https://www.11ty.dev/docs/pagination/#paging-a-collection) with `size: 1` to render the content using a different template, but both `.content` and `data.content` are empty in the pagination object.

Even if I could access `.content`, I have a feeling that it would be rendered HTML using `layout1.njk`, so it wouldn't be able to fit nicely into `layout2.njk`.

# The solution - use `.templateContent|safe`

darth_mall helped me work this out in the [11ty Discord](https://www.11ty.dev/blog/discord/) - I needed to use `.templateContent|safe` in the Markdown file when paginating (`src/using-layout2.md`).

This means that we can generate multiple outputs from the same content.