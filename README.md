# Protocode Documentation Pages

## Description

This project contains pages data used by our documentation site learn.protocode.tech.

## Getting started

All the structure is in `pages/` folder.

It contains chapters at first level (folders containing files `chapter.${LOCALE}.md`), 
which contains themselves articles (subfolders containing files `docs.${LOCALE}.md`).

So in each folder, each chapter and each article should be duplicated with the locale fitting its content (*fr*, and *en* at the moment).

Each `.md` file is structured this way: YAML metadata in the heading enclosed by `---`, and pure markdown below that.
Here is an example:

```markdown
---
title: My page title
---

# My page title

My page description leading to an [external page](https://external.ext/slug) 
```

## Roadmap

- [ ] [Finishing the french documentation]
- [ ] [Add english translation]
- [ ] [Add videos]

## Contributing

Feel free to make any suggestions or PR! Your help is appreciated :) 

## License

This project is under MIT Licence.
