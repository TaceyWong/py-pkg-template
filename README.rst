======================
Python Package Template （cookiecutter_）
======================

.. image:: https://pyup.io/repos/github/taceywong/py-pkg-template/shield.svg
    :target: https://pyup.io/repos/github/taceywong/py-pkg-template/
    :alt: Updates

.. image:: https://travis-ci.org/taceywong/py-pkg-template.svg?branch=master
    :target: https://travis-ci.org/github/taceywong/py-pkg-template
    :alt: Build Status

.. image:: https://readthedocs.org/projects/py-pkg-template/badge/?version=latest
    :target: https://py-pkg-template.readthedocs.io/en/latest/?badge=latest
    :alt: Documentation Status

Python包 Cookiecutter_ 模板

* GitHub 仓库: https://github.com/taceywong/py-pkg-template/
* 文档: https://py-pkg-template.readthedocs.io/
* 开源协议: BSD license

特性&功能
--------

* Testing setup with ``unittest`` and ``python setup.py test`` or ``pytest``
* Travis-CI_: Ready for Travis Continuous Integration testing
* Tox_ testing: Setup to easily test for Python 3.5, 3.6, 3.7, 3.8
* Sphinx_ docs: Documentation ready for generation with, for example, `Read the Docs`_
* bump2version_: Pre-configured version bumping with a single command
* Auto-release to PyPI_ when you push a new tag to master (optional)
* Command line interface using Click (optional)

.. _Cookiecutter: https://github.com/cookiecutter/cookiecutter

构建状态
-------------

Linux:

.. image:: https://img.shields.io/travis/taceywong/py-pkg-template.svg
    :target: https://travis-ci.org/taceywong/py-pkg-template
    :alt: Linux build status on Travis CI

Windows:

.. image:: https://ci.appveyor.com/api/projects/status/github/taceywong/py-pkg-template?branch=master&svg=true
    :target: https://ci.appveyor.com/project/taceywong/py-pkg-template/branch/master
    :alt: Windows build status on Appveyor

快速开始
----------

Install the latest Cookiecutter if you haven't installed it yet (this requires
Cookiecutter 1.4.0 or higher)::

    pip install -U cookiecutter

生成一个Python包项目::

    cookiecutter https://github.com/taceywong/py-pkg-template.git

Then:

* Create a repo and put it there.
* Add the repo to your Travis-CI_ account.
* Install the dev requirements into a virtualenv. (``pip install -r requirements_dev.txt``)
* Register_ your project with PyPI.
* Run the Travis CLI command ``travis encrypt --add deploy.password`` to encrypt your PyPI password in Travis config
  and activate automated deployment on PyPI when you push a new tag to master branch.
* Add the repo to your `Read the Docs`_ account + turn on the Read the Docs service hook.
* Release your package by pushing a new tag to master.
* Add a ``requirements.txt`` file that specifies the packages you will need for
  your project and their versions. For more info see the `pip docs for requirements files`_.
* Activate your project on `pyup.io`_.

.. _`pip docs for requirements files`: https://pip.pypa.io/en/stable/user_guide/#requirements-files
.. _Register: https://packaging.python.org/tutorials/packaging-projects/#uploading-the-distribution-archives

For more details, see the `cookiecutter-pypackage tutorial`_.

.. _`py-pkg-template tutorial`: https://py-pkg-template.readthedocs.io/en/latest/tutorial.html







.. _Travis-CI: http://travis-ci.org/
.. _Tox: http://testrun.org/tox/
.. _Sphinx: http://sphinx-doc.org/
.. _Read the Docs: https://readthedocs.io/
.. _`pyup.io`: https://pyup.io/
.. _bump2version: https://github.com/c4urself/bump2version
.. _Punch: https://github.com/lgiordani/punch
.. _Poetry: https://python-poetry.org/
.. _PyPi: https://pypi.python.org/pypi

