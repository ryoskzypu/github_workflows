# Reusable GitHub workflows

## Workflows

### perl-test

Runs Perl tests on Linux using [docker-perl-tester](https://github.com/Perl/docker-perl-tester)
images. Automagically creates matrix for every perl since v5.24.0 up to newest.

Based on:

- https://github.com/perl-actions/github-workflows
- https://github.com/xsawyerx/module-starter/blob/master/.github/workflows/test.yml

#### Input parameters

- `since-perl`: include only perls since given version (starting with v5.8.0)
- `to-perl`: include only perls up to given version
- `with-devel`: include `devel` as well

> [!NOTE]
> `since-perl` and `to-perl` use values from https://github.com/Perl/docker-perl-tester#using-docker-images-for-your-projects.

#### Examples

```
name: 'CI'

on:

  ...

jobs:
  call-perl-test:
    uses: ryoskzypu/github_workflows/.github/workflows/perl-test.yml@main
    with:
      since-perl: v5.40.0
      with-devel: true
```

See [caller example](https://github.com/ryoskzypu/App-prog/blob/main/.github/workflows/test.yml).

### See also

- https://perlmaven.com/what-is-ci
- https://perlhacks.com/2024/01/github-actions-for-perl-development/
- https://docs.github.com/en/actions/how-tos/reuse-automations/reuse-workflows
- https://github.com/perl-actions/perl-versions
- https://github.com/FGasper/perl-github-action-tips
