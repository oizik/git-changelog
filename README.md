# git-changelog

**NOTE:** This repo is a slightly modified version of [git-changelog](https://github.com/pawamoy/git-changelog). It allows to specify the release type at command line using `-r` flat, or force the version using `-f` flag instead of guessing it.

Automatic Changelog generator using Jinja2 templates. From git logs to change logs.

## Features

- [Jinja2][jinja2] templates!
  You get full control over the rendering.
  Built-in [Keep a Changelog][keep-a-changelog] and [Angular][angular] templates
  (also see [Conventional Changelog][conventional-changelog]).
- Commit styles/conventions parsing.
  Built-in [Angular][angular-style], [Conventional Commit][conventional-commit], [Atom][atom-style] and basic styles.
- Git service/provider agnostic,
  plus references parsing (issues, commits, etc.).
  Built-in [GitHub][github-refs] and [Gitlab][gitlab-refs] support.
- Understands [Semantic Versioning][semantic-versioning]:
  major/minor/patch for versions and commits.
  Guesses next version based on last commits.

- Todo:
  - [Plugin architecture][issue-19],
    to support more commit styles and git services.
  - [Template context injection][issue-17],
    to furthermore customize how your changelog will be rendered.
  - [Easy access to "Breaking Changes"][issue-14] in the templates.
  - [Update changelog in-place][issue-15], paired with
    [commits/dates/versions range limitation ability][issue-16].

[jinja2]:                 http://jinja.pocoo.org/
[keep-a-changelog]:       http://keepachangelog.com/en/1.0.0/
[angular]:                https://github.com/angular/angular/blob/master/CHANGELOG.md
[conventional-changelog]: https://github.com/conventional-changelog/conventional-changelog
[semantic-versioning]:    http://semver.org/spec/v2.0.0.html
[atom-style]:             https://github.com/atom/atom/blob/master/CONTRIBUTING.md#git-commit-messages
[angular-style]:          https://github.com/angular/angular/blob/master/CONTRIBUTING.md#commit
[conventional-commit]:    https://www.conventionalcommits.org/en/v1.0.0/
[github-refs]:            https://help.github.com/articles/autolinked-references-and-urls/
[gitlab-refs]:            https://docs.gitlab.com/ce/user/markdown.html#special-gitlab-references

[issue-14]: https://github.com/pawamoy/git-changelog/issues/14
[issue-15]: https://github.com/pawamoy/git-changelog/issues/15
[issue-16]: https://github.com/pawamoy/git-changelog/issues/16
[issue-17]: https://github.com/pawamoy/git-changelog/issues/17
[issue-19]: https://github.com/pawamoy/git-changelog/issues/19

## Installation

With `pip`:

```bash
pip install git-changelog
```

With [`pipx`](https://github.com/pipxproject/pipx):

```bash
python3.7 -m pip install --user pipx
pipx install git-changelog
```

## Usage (command-line)

```
usage: git-changelog [-h] [-o OUTPUT] [-s {angular,atom,basic}]
                     [-t {angular,keepachangelog}] [-v]
                     REPOSITORY

Command line tool for git-changelog Python package.

positional arguments:
  REPOSITORY            The repository path, relative or absolute.

optional arguments:
  -h, --help            Show this help message and exit.
  -o OUTPUT, --output OUTPUT
                        Output to given file. Default: stdout.
  -s {angular,atom,basic}, --style {angular,atom,basic}
                        The commit style to match against.
  -t {angular,keepachangelog}, --template {angular,keepachangelog}
                        The Jinja2 template to use. Prefix with "path:" to
                        specify the path to a directory containing a file
                        named "changelog.md".
  -f VERSION, --force VERSION
                        Force a specific version number e.g. v1.5.9.
                        This setting takes precedence over the release type.
  -r {patch,minor,major}, --release {patch,minor,major}
                        The release type to use for the next version,
                        this settings takes precedence over over guessing next version.
  -v, --version         Show the current version of the program and exit.

```
