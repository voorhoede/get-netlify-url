# Get Netlify URL
This GitHub action gets the Netlify deployment URL at the current branch.

## Basic example
```yaml
- name: 'Get Netlify URL'
  uses: voorhoede/get-netlify-url@v2
  id: get-netlify-url

- name : 'Log retrieved URL'
  run: 'echo ${{ steps.get-netlify-url.outputs.url }}'
```

## Inputs

### `site-name`
Netlify site name, defaults to repository name.

### Password protection
Optional input to authenticate on [Netlify protected pages](https://docs.netlify.com/visitor-access/password-protection/) by adding basic authentication to the URL.

### `basic-auth-username`
Basic authentication username.

### `basic-auth-password`
Basic authentication password.

## Outputs

### `url`
The Netlify deployment URL.

## Usage examples

### [Cypress](https://github.com/cypress-io/github-action)
```yaml
name: Audit Preview Deploys

jobs:
  integration:
    name: Run integration tests
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: voorhoede/get-netlify-url@v2
        id: get-netlify-url
      - uses: cypress-io/github-action@v1
        env:
          CYPRESS_BASE_URL: ${{ steps.get-netlify-url.outputs.url }}
        with:
          wait-on: ${{ steps.get-netlify-url.outputs.url }}
```
