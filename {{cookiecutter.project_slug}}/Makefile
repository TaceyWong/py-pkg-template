.PHONY: clean clean-test clean-pyc clean-build docs help
.DEFAULT_GOAL := help

define BROWSER_PYSCRIPT
import os, webbrowser, sys

from urllib.request import pathname2url

webbrowser.open("file://" + pathname2url(os.path.abspath(sys.argv[1])))
endef
export BROWSER_PYSCRIPT

define PRINT_HELP_PYSCRIPT
import re, sys

for line in sys.stdin:
	match = re.match(r'^([a-zA-Z_-]+):.*?## (.*)$$', line)
	if match:
		target, help = match.groups()
		print("%-20s %s" % (target, help))
endef
export PRINT_HELP_PYSCRIPT

BROWSER := python -c "$$BROWSER_PYSCRIPT"

help:
	@python -c "$$PRINT_HELP_PYSCRIPT" < $(MAKEFILE_LIST)

clean: clean-build clean-pyc clean-test ## 清除所有build, test等等的遗留

clean-build: ## 清除build遗留
	rm -fr build/
	rm -fr dist/
	rm -fr .eggs/
	find . -name '*.egg-info' -exec rm -fr {} +
	find . -name '*.egg' -exec rm -f {} +

clean-pyc: ## 清除.pyc .pyo等等
	find . -name '*.pyc' -exec rm -f {} +
	find . -name '*.pyo' -exec rm -f {} +
	find . -name '*~' -exec rm -f {} +
	find . -name '__pycache__' -exec rm -fr {} +

clean-test: ## 清除测试遗留
	rm -fr .tox/
	rm -f .coverage
	rm -fr htmlcov/
	rm -fr .pytest_cache

lint: ## flake8检测代码风格
	flake8 xacs tests

test: ## 快速测试代码
	pytest

test-all: ## 使用各个版本的Python测试代码
	tox

coverage: ## 生成代码覆盖报告
	coverage run --source xacs -m pytest
	coverage report -m
	coverage html
	$(BROWSER) htmlcov/index.html

docs: ## 生成 Sphinx HTML 文档, 包括 API 文档
	rm -f docs/xacs.rst
	rm -f docs/modules.rst
	sphinx-apidoc -o docs/ xacs
	rm -f docs/xacs.cli.rst
	$(MAKE) -C docs clean
	$(MAKE) -C docs html
	$(BROWSER) docs/_build/html/index.html

servedocs: docs ## 编译文档并查看变更
	watchmedo shell-command -p '*.rst' -c '$(MAKE) -C docs html' -R -D .

release: dist ## 发布到pypi
	python -m twine upload dist/*

dist: clean ## 构建Python包
	python setup.py sdist
	python setup.py bdist_wheel
	ls -l dist

install: clean ## 安装Python包
	python setup.py install

write-dep: ## 依赖包写到文件（先激活venv）
	 echo " -i https://mirrors.aliyun.com/pypi/simple/" > requirements.txt
	 pip3 freeze >> requirements.txt
