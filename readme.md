# Get Netlify URL
This GitHub action gets the Netlify deployment URL at the current branch.

## Basic example
```yaml
- name: 'Get Netlify URL'
  uses: voorhoede/get-netlify-url
  id: get-netlify-url

- name : 'Log retrieved URL'
  run: 'echo ${{ steps.get-netlify-url.outputs.url }}'
```

## Inputs

### `site-name`
Netlify site name, defaults to repository name.

### `basic-auth-username`
Basic authentication username.

### `basic-auth-password`
Basic authentication password.

## Outputs

### `url`
The Netlify deployment URL.

