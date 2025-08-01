# Notes and thoughts

- Interested in what it uses for metadata state, is there a analog to `.git`?
  - How does this work in conjunction with the `git`
    - A: side by side, with a lot of `npm` like inspirations
      - `pyproject.toml` in the place of a `package.json`: [link](https://github.com/frankhereford/discovery_day_aug_2025/blob/main/pyproject.toml)
      - `.python-version` in the place of `.nvmrc`
      - `uv.lock` as `package-lock.json`: [link](https://github.com/frankhereford/discovery_day_aug_2025/blob/main/pyproject.toml)
- Handles `venv` really well
  - you can `source` into it to configure your shell to use the local environment
  - or you can `uv python` as your python invocation and `uv` will use the environment only for the execution of the script without having modified your current shell's configuration
- 🏎️ installed `notebook` and all its dependencies in < 2 seconds, easily

## Goals

- Stand up a local Jupyter Notebook and manage using additional libraries
  - Try not to mix technologies (`pip` and `uv`)
- make it work with beam.ai too

## Pros & Cons

### Pros

- Found all my pre-installed versions of python
- Some black magic with `.git` to ignore the `.venv` but not require a `.gitignore`
