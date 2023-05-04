# Notebook to `html` for `Jekyll`

Convert a `.ipnb` to `.html` for `Jekyll`.

You can find this package at [here][github-repo].

## How to use

### Preparation

1. Add this repository into your main directory.
2. Exclude it in `_config.yml` like the following.

   ```sh
    exclude:
        - notebook-to-html-jekyll
   ```

3. Ignore it if you use git by running `echo "\nnotebook-to-html-jekyll\n" >> .gitignore`.

4. Run from your main directory  
   `python3 notebook-to-html-jekyll --prepare`.

Now, you are ready to convert a `.ipynb` to a `.html` file for `Jekyll`.

### Convert files

Convert a `.ipynb` file to `.html` by
running  
`python3 notebook-to-html-jekyll --convert path/to/your/file.ipynb`  

Get the `.html` file in the same path as your `.ipynb` file.

Include your notebook in your jekyll site using the following

```sh
---

{% include_relative notebook-file-name.html %}

---
```

## Contents

- `_includes`
  - `matjax-setup.html`
  - `notebook-css.html`
- `prepare`
- `convert`
- `__init__.py`

## Roadmap

### `prepare`

- [ ] add includes to `_includes/`  
  `cp notebook-to-jekyll/_includes/* _includes/`

- [ ] add layout to `_layout/`
  - [ ] for `layout.html` in `_layout/` directory
    - [ ] run `cp _layout/{{layout}}.html _layout/{{layout}}-notebook.html`
    - [ ] if `_layout/{{layout}}-notebook.html` contains `layout: {layout-name}`
      - [ ] append `-notebook` to `layout: {layout-name}` (i.e. `layout: {layout-name}-notebook`)
    - [ ] else
      - [ ] edit `<head ... </head>` of `_layout/{{layout}}-notebook.html`
        - [ ] add `{% include matjax-setup.html %}`
        - [ ] add `{% include noteboo-css.html %}`

### `convert`

- [ ] Make Jekyll's `.html` from `.ipynb`
  - [ ] run `jupyter-nbconvert path/input/file.ipynb --to html`  
    It will generate `path/input/file.html`.
  - [ ] Edit `path/input/file.html`
    - [ ] delete everything except `<body ... </body>`
    - [ ] replace `body` tag with `div` tag.
    - [ ] put `{{`,`}}`, `{%` and `%}`  in `{% raw %} ... {% endraw %}` block.

## Author

[github-repo]: https://github.com:aheritianad/notebook-to-html-jekyll.git  
