# heroku-buildpack-tower

A Heroku buildpack for inserting SSH keys based on Heroku config vars and creating an SSH configuration file with host aliases. Used to let Tower websites pull in npm and Composer dependencies from private GitHub repositories.

## Usage

Set the Heroku config vars `SSH_KEY_COMPOSER` and `SSH_KEY_NPM` to the private keys corresponding to the public keys added as deploy keys to the private repositories.

These will be written to `~/.ssh/id_rsa-composer` and `~/.ssh/id_rsa-npm` respectively.

An SSH configuration file will be written to `~/.ssh/config`, setting up GitHub aliases using each of these keys. These aliases — `github-composer` and `github-npm` — can then be used instead of `github.com` in the dependency URLs to ensure the correct keys are used.
