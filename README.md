# README

Repository with example setup to reproduce issue with serving Angular application on a subpath (`/ng16-base-href/`, `/ng17-base-href/`). Repo contains two setups:

- ng16-base-href: example app with Angular `v16.2.12`
- ng17-base-href: example app with Angular `v17.0.6`

Start the application by entering in each directory and run:

```sh
npm install
npm start
```

This will start the apps:

- http://localhost:4200/ng16-base-href/
- http://localhost:4201/ng17-base-href/

Both apps are configured to serve on a subpath (`/ng16-base-href/`, `/ng17-base-href/`), this is configured by:

- invoking `ng serve` with the `--serve-path '/ng1*-base-href/'` flag
- setting the `<base href="./">` in `src/index.html` 

The ng16-base-href application behaves as expected.

The ng17-base-href application does not behave as expected:

- The application "redirects" from `http://localhost:4201/ng17-base-href/` to `http://localhost:4201/` (in the network tab there is not real redirect, seems the window.location is modified)
- An error is logged to the debug console:

    ```
    ERROR Error: NG04002: Cannot match any routes. URL Segment: 'ng17-base-href'
    ```
