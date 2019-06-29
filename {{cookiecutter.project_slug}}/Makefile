.PHONY: develop teardown env launch-app clean test flake8

VENV_DIR = .venv
WITH_VENV = . $(VENV_DIR)/bin/activate

launch-app: env-exist 

env: requirements.txt
	test -d $(VENV_DIR) || virtualenv -p python3 $(VENV_DIR)
	$(VENV_DIR)/bin/pip3 install -r requirements.txt
	touch $(VENV_DIR)/bin/

env-exist:
	test -f $(VENV_DIR)/bin/activate || $(MAKE) develop

develop: env setup.py
	$(WITH_VENV) && python setup.py develop

teardown:
	rm -rf .venv/

flake8: env-exist
# 	$(WITH_VENV) && flake8 {{cookiecutter.project_slug}}

test: env-exist
# 	$(WITH_VENV) && pytest

clean:
	find . |  grep -E "(__pycache__|\.pyc$\)" | xargs rm -rf
	rm -rf {{cookiecutter.project_slug}}.egg-info/
	rm -rf *.pyc
	rm -rf {{cookiecutter.project_slug}}/.pytest_cache/

docs: env-exist
# 	$(WITH_VENV) && cd docs && $(MAKE) html
