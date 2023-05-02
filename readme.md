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
  - [ ] make `post-with-notebook.html`
    - [ ] run `cp _layout/default.html _layout/post-with-notebook.html`
    - [ ] edit `<head ... </head>` of `_layout/post-with-notebook.html`
      - [ ] add `{% include matjax-setup.html %}`
      - [ ] add `{% include noteboo-css.html %}`
    - [ ] [Optional] Make it like post content
      - [ ] edit `<body ... </body>` of `_layout/post-with-notebook.html`
        - [ ] retrieve `content_setup = _layout/post.html`
        - [ ] replace `{{ content }}` in `_layout/post-with-notebook.html` with `content_setup`

### `convert`

- [ ] Make Jekyll's `.html` from `.ipynb`
  - [ ] run `jupyter-nbconvert path/input/file.ipynb --to html`  
    It will generate `path/input/file.html`.
  - [ ] Edit `path/input/file.html`
    - [ ] delete everything except `<body ... </body>`
    - [ ] replace `body` tag with `div` tag.
    - [ ] put `{{`,`}}`, `{%` and `%}`  in `{% raw %} ... {% endraw %}` block.
    - [ ] add  

        ```sh
        ---
        layout: post-with-notebook
        ---
        ```

        at the top.

## Author

[github-repo]: https://github.com:aheritianad/notebook-to-html-jekyll.git  
