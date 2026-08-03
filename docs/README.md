# Docs handbook

> Information about the API docs.

## Overview

## Documentation generator

- The generation of the docs is implemented using [Sphinx](https://www.sphinx-doc.org/en/master/) with extensions listed in `extensions` in `docs/conf.py`.
- Documentation is automatically generated from docstrings and help-text (CLI) in the source code of `pixelator`.
- Docstrings are formatted according to [Google conventions for docstrings](https://google.github.io/styleguide/pyguide.html#38-comments-and-docstrings).
- Where possible, internal names have cross-referencing pointing to a page in the docs, and external names map to the public external documentation site. Links to stable external documentation are kept in `intersphinx_mapping` in `docs/conf.py`.
- The `__all__` lists in the package `__init__.py`-files determine what name-links are shown on the parent package page in the API reference.
- CLI docs uses [sphinx-click](https://sphinx-click.readthedocs.io/en/latest/).



## Inclusion

`autoapi` inclusion is mainly determined by `autoapi_options` and `autoapi_ignore` in `docs/conf.py`. Some options worth mentioning include:

- Imported members (`imported-members`) are intentionally included in the docs generation via `autoapi_options`.
- Private members (`private-members`) are not included via `autoapi_options`.
- Parts of the codebase, e.g. names related to MPX are ignored via `autoapi_ignore`.



## Maintenance

- Updating/adding docstrings and help-text in source code at changes.
- The overview page (`overview.rst`) lists some primary entry points of the API. Additions to this page are added manually.
- `intersphinx_mapping` in `docs/conf.py` lists the URLs for documentation of external names used for cross-referencing. This list is maintained manually.



## Deployment

- Building and deploying the docs is handled by `deploy-docs.yml`.
- The docs are built and deployed on release and on manual dispatch, and are built (not deployed) on PR.
- The docs are deployed via [GitHub Pages](https://docs.github.com/en/pages)



## Development

1. Install the docs dependency group: `uv sync --group docs`
2. Clean up and build the HTML (log warnings):

```
rm -rf docs/_build docs/api/generated && uv run sphinx-build -b html docs docs/_build/html --keep-going -n -w docs/_build/sphinx-warnings.log
```

1. Open `docs/_build/html/index.html`.



## Other

- The relevant sections of this document (docs/README.md) should be updated if changes are made.



## References

- [Sphinx documentation](https://www.sphinx-doc.org/en/master/)
- [AutoAPI documentation](https://sphinx-autoapi.readthedocs.io/en/latest/index.html)
- [sphinx-click](https://sphinx-click.readthedocs.io/en/latest/)
- [Google docstrings](https://google.github.io/styleguide/pyguide.html#38-comments-and-docstrings)

