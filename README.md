# Getting Started with Create React App

This project was bootstrapped with [Create React
App](https://github.com/facebook/create-react-app). It was intentionally
created with React 17, which contains several vulnerabilities, to demonstrate
the utility of SBOMs and scanning for identifying vulnerabilities.

## Building with buildpack
To containerize this app with Paketo buildpacks, run
```
pack build frontend-nginx \
  --buildpack paketo-buildpacks/web-servers \
  --buildpack paketo-buildpacks/source-removal \
  --env BP_NODE_RUN_SCRIPTS=build \
  --env BP_WEB_SERVER=nginx \
  --env BP_WEB_SERVER_ROOT=build \
  --env BP_INCLUDE_FILES=*.conf:build/* \
  --sbom-output-dir ./sbom-content
```

## Looking for vulnerabilities
1. With `docker scan`
```
docker scan frontend-nginx
```

2. Scan the image with `grype`
```
grype frontend-nginx
```

3. Scan the SBOM outputted by the build with `grype`
```
grype sbom:sbom-content/build/paketo-buildpacks_npm-install/build-modules/sbom.syft.json
```

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

The page will reload when you make changes.\
You may also see any lint errors in the console.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: [https://facebook.github.io/create-react-app/docs/code-splitting](https://facebook.github.io/create-react-app/docs/code-splitting)

### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `npm run build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)
