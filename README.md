# Reusable GitHub workflows

## Workflows

### perl-test

Runs Perl tests on Linux using [docker-perl-tester](https://github.com/Perl/docker-perl-tester)
images. Automagically creates matrix for every perl since v5.24.0 up to newest.

Based on:

- https://github.com/perl-actions/github-workflows
- https://github.com/xsawyerx/module-starter/blob/master/.github/workflows/test.yml

#### Input parameters

- `since-perl`: include only perls since given version (starting with v5.24.0)
- `to-perl`: include only perls up to given version
- `with-devel`: include `devel` as well
- `coverage`: if true, check the Perl code test coverage on `latest` and report the results to [Coveralls.io](https://coveralls.io)
- `critic`: if true, run `perlcritic` against the distribution files with [Test::Perl::Critic](https://metacpan.org/pod/Test::Perl::Critic)

See [perl-version parameters](https://github.com/perl-actions/perl-versions?tab=readme-ov-file#parameters) for details.

> [!NOTE]
> - `since-perl` and `to-perl` use values from [docker-perl-tester](https://github.com/Perl/docker-perl-tester#using-docker-images-for-your-projects).
> - `critic` requires a *critic.t* file in the *xt* directory. See [critic.t example](https://github.com/ryoskzypu/App-prog/blob/main/xt/critic.t).

> [!TIP]
> To check if distribution files have been run through `perltidy`, enable [CodeLayout::RequireTidyCode](https://metacpan.org/pod/Perl::Critic::Policy::CodeLayout::RequireTidyCode) in [perlcritic config file](https://metacpan.org/dist/Perl-Critic/view/bin/perlcritic#CONFIGURATION).

#### Examples

```yaml
name: 'CI'

on:

  ...

jobs:
  call-perl-test:
    uses: ryoskzypu/github_workflows/.github/workflows/perl-test.yml@main
    with:
      since-perl: 'v5.40.0'
      with-devel: true
      coverage: true
```

See [caller example](https://github.com/ryoskzypu/App-prog/blob/main/.github/workflows/ci.yml).

### See also

- https://perlmaven.com/what-is-ci
- https://perlhacks.com/2024/01/github-actions-for-perl-development/
- https://docs.github.com/en/actions/how-tos/reuse-automations/reuse-workflows
- https://github.com/perl-actions/install-with-cpanm
- https://github.com/FGasper/perl-github-action-tips
- https://metacpan.org/pod/Devel::Cover::Report::Coveralls
- https://metacpan.org/pod/perlcritic
- https://metacpan.org/pod/perltidy
