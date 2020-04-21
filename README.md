# Pre-commit hooks

This repo defines Git pre-commit hooks intended for use with [pre-commit](http://pre-commit.com/). The currently
supported hooks are:

* **terraform-fmt**: Automatically run `terraform fmt` on all Terraform code (`*.tf` files).
* **terraform-validate**: Automatically run `terraform validate` on all Terraform code (`*.tf` files).
* **tflint**: Automatically run [`tflint`](https://github.com/terraform-linters/tflint) on all Terraform code (`*.tf` files).
* **shellcheck**: Run [`shellcheck`](https://www.shellcheck.net/) to lint files that contain a bash [shebang](https://en.wikipedia.org/wiki/Shebang_(Unix)).
* **gofmt**: Automatically run `gofmt` on all Golang code (`*.go` files).
* **golint**: Automatically run `golint` on all Golang code (`*.go` files).
* **yapf**: Automatically run [`yapf`](https://github.com/google/yapf) on all python code (`*.py` files).
* **helmlint** Automatically run [`helm lint`](https://github.com/helm/helm/blob/master/docs/helm/helm_lint.md) on your Helm chart files. [See caveats here](#helm-lint-caveats).
* **markdown-link-check** Automatically run [markdown-link-check](https://github.com/tcort/markdown-link-check) on
  markdown doc files.




## General Usage

In each of your repos, add a file called `.pre-commit-config.yaml` with the following contents:

```yaml
repos:
  - repo: https://github.com/bantrain/pre-commit
    rev: <VERSION> # Get the latest from: https://github.com/bantrain/pre-commit/releases
    hooks:
      - id: terraform-fmt
      - id: terraform-validate
      - id: tflint
      - id: shellcheck
      - id: gofmt
      - id: golint
```

Next, have every developer: 

1. Install [pre-commit](http://pre-commit.com/). E.g. `brew install pre-commit`.
1. Run `pre-commit install` in the repo.

That’s it! Now every time you commit a code change (`.tf` file), the hooks in the `hooks:` config will execute.