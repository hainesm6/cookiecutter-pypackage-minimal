# Modified version of [cookiecutter-pypackage-minimal](https://github.com/kragniz/cookiecutter-pypackage-minimal)

Several changes were made to [cookiecutter-pypackage-minimal](https://github.com/kragniz/cookiecutter-pypackage-minimal).

Usage
-----

    pip install cookiecutter
    git clone https://github.com/kragniz/cookiecutter-pypackage-minimal.git
    cookiecutter cookiecutter-pypackage-minimal/

You should then change the classifiers in `{{ package_name }}/setup.py`. The full list of PyPI classifiers can be found [here](https://pypi.org/classifiers/).

Fill out the README, and - if necessary - [choose a license](https://choosealicense.com/) for the project.

To ensure builds pass a `requirements.txt` file is required and can be generated as follows:

```sh
pip freeze > requirements.txt
```

Explanation
-----------

### LICENSE

* **MIT license by default**
  This template provides you the classic [MIT](https://choosealicense.com/licenses/mit/) licence: it lets people do almost anything they want with your project, including to make and distribute closed source versions.
  If you [choose another license](https://choosealicense.com/), you also need to update the `{{ package_name }}/setup.py` file:
  adjust the `classifiers` and `license` fields accordingly.
* **A license is a requirement**
  Nowadays, people who want to use your library/application want to make sure they can do it legally.
  If your library is a private library, you can use a private license. In the `{{ package_name }}/setup.py` file, set `license="Proprietary"`, and choose `'License :: Other/Proprietary License'` in the trove classifiers.

### `setup.py`

* **Use setuptools**
  It's the standard packaging library for Python. `distribute` has merged back into `setuptools`, and `distutils` is less capable.
* **setup.py should not import anything from the package**
  When installing from source, the user may not have the packages dependencies installed, and importing the package is likely to raise an `ImportError`.

### Testing

* **Uses [pytest](https://docs.pytest.org) as the default test runner**
  This can be changed easily, though pytest is a easier, more powerful test library and runner than the standard library's unittest.
* **`tests` directory should not be a package**
  The `tests` directory should not be a Python package unless you want to define some fixtures.
  But the best practices are to use [PyTest fixtures](https://docs.pytest.org/en/latest/fixture.html) which provides a better solution.
  Therefore, the `tests` directory has no `__init__.py` file.
