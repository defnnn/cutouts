SHELL := /bin/bash

.PHONY: cutout

menu:
	@perl -ne 'printf("%10s: %s\n","$$1","$$2") if m{^([\w+-]+):[^#]+#\s(.+)$$}' Makefile

cutout:
	rm -rf cutout
	cookiecutter --no-input --directory t/python gh:defn/cutouts \
		organization="{{cookiecutter.organization}}" \
		project_name="{{cookiecutter.project_name}}" \
		repo="{{cookiecutter.repo}}" \
		repo_cache="{{cookiecutter.repo_cache}}"
	rsync -ia cutout/. .
	rm -rf cutout
	git difftool --tool=vimdiff -y
