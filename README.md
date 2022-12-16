# My notes:

Register for an account on test.pypi, and get an API token.

https://packaging.python.org/en/latest/tutorials/packaging-projects/#generating-distribution-archives

```sh
# update the pyproject.toml [project] name (to be the package name)
python3 -m pip install --upgrade build
# go to folder that contains pyproject.toml and run this:
python3 -m build
```

https://packaging.python.org/en/latest/tutorials/packaging-projects/#uploading-the-distribution-archives

```sh
python3 -m pip install --upgrade twine
# go folder containing dist and run this:
python3 -m twine upload --repository testpypi dist/*
# for username, literally enter username as __token__
# for password, use your API key from your test.pypi account, including pypi- prefix
# https://test.pypi.org/search/?q=example_package_hchiam
# https://test.pypi.org/project/example-package-hchiam/
```

(more steps if you want to test the test-only version of your package: https://test.pypi.org/project/example-package-hchiam/)

To upload the production-ready version of your package: (pypi requires a separate registration and API key set up from the test.pypi site)

```sh
python3 -m twine upload dist/*
# for username, still literaly enter __token__
# for password, use your other API key from your pypi account, including pypi- prefix
# https://pypi.org/search/?q=example_package_hchiam
# https://pypi.org/project/example-package-hchiam/
```

```sh
# python3 -m pip install [your-package]
python3 -m pip install example_package_hchiam
```

`/tests/test_example.py` shows a good example of how the package will be used by users, where you can see a method from an inner/non-`__init__` file, e.g.:

```py
from example_package_hchiam.example import add_one
```

# A sample Python project

![Python Logo](https://www.python.org/static/community_logos/python-logo.png "Sample inline image")

A sample project that exists as an aid to the [Python Packaging User
Guide][packaging guide]'s [Tutorial on Packaging and Distributing
Projects][distribution tutorial].

This project does not aim to cover best practices for Python project
development as a whole. For example, it does not provide guidance or tool
recommendations for version control, documentation, or testing.

[The source for this project is available here][src].

The metadata for a Python project is defined in the `pyproject.toml` file,
an example of which is included in this project. You should edit this file
accordingly to adapt this sample project to your needs.

---

This is the README file for the project.

The file should use UTF-8 encoding and can be written using
[reStructuredText][rst] or [markdown][md use] with the appropriate [key set][md use]. It will be used to generate the project webpage on PyPI and will be
displayed as the project homepage on common code-hosting services, and should be
written for that purpose.

Typical contents for this file would include an overview of the project, basic
usage examples, etc. Generally, including the project changelog in here is not a
good idea, although a simple “What's New” section for the most recent version
may be appropriate.

[packaging guide]: https://packaging.python.org
[distribution tutorial]: https://packaging.python.org/tutorials/packaging-projects/
[src]: https://github.com/pypa/sampleproject
[rst]: http://docutils.sourceforge.net/rst.html
[md]: https://tools.ietf.org/html/rfc7764#section-3.5 "CommonMark variant"
[md use]: https://packaging.python.org/specifications/core-metadata/#description-content-type-optional
