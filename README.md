# Pre commit Python

- Install dependencies

```bash
pip install -r requirements.txt
# This will install
# pre-commit
# pylint
# autopep8
# yamllint
```

- Basic configuration for .pre-commit-config.yaml

```yaml
# Adjust the .venv path properly if you are using python virtual environment
---
repos:
  - repo: local
    hooks:

      - id: pylint
        name: pylint
        entry: ./.venv/bin/pylint
        language: system
        types: [python]
        exclude: '^\.venv/'

      - id: autopep8
        name: autopep8
        entry: ./.venv/bin/autopep8
        language: system
        types: [python]
        args: [--aggressive, --aggressive, --in-place]
        exclude: '^\.venv/'

      - id: yamllint
        name: yamllint
        entry: ./.venv/bin/yamllint
        language: system
        types: [yaml]
        exclude: '^\.venv/'
```

- Run out of a commit 

```bash
pre-commit run --all-files
```

- Output

```bash
pylint...................................................................Passed
autopep8.................................................................Passed
yamllint.................................................................Passed
```

- Make changes to your files and try to commit. <!--  -->Automatic pre-commit run will happen