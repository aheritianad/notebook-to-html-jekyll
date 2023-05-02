# Notebook to `html` for `Jekyll`

Convert a `.ipnb` to `.html` for `Jekyll`.

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
    - [ ] add  

        ```sh
        ---
        layout: post-with-notebook
        ---
        ```

        at the top.
