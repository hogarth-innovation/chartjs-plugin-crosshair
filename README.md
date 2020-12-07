
<div align="center">
    <centering>
    <img src="header.png" width='600px'/>
    </centering>
</div>


[Chart.js](http://www.chartjs.org/) plugin to draw vertical crosshair, zoom, interpolate values and sync chart interactions.

Requires [Chart.js](https://github.com/chartjs/Chart.js/releases) **2.6.0** or later.

## Documentation

- [Installation](https://chartjs-plugin-crosshair.netlify.com/installation)
- [Options](https://chartjs-plugin-crosshair.netlify.com/options)
- [Samples](https://chartjs-plugin-crosshair.netlify.com/samples)

## Example

```javascript
new Chart(ctx, {
  // ... data ...
  options: {
    // ... other options ...
    tooltips: {
      mode: 'interpolate',
      intersect: false
    },
    plugins: {
      crosshair: {
        line: {
          color: '#F66',  // crosshair line color
          width: 1        // crosshair line width
        },
        sync: {
          enabled: true,            // enable trace line syncing with other charts
          group: 1,                 // chart group
          suppressTooltips: false   // suppress tooltips when showing a synced tracer
        },
        zoom: {
          enabled: true,                                      // enable zooming
          zoomboxBackgroundColor: 'rgba(66,133,244,0.2)',     // background color of zoom box 
          zoomboxBorderColor: '#48F',                         // border color of zoom box
          zoomButtonText: 'Reset Zoom',                       // reset zoom button text
          zoomButtonClass: 'reset-zoom',                      // reset zoom button class
        },
        callbacks: {
          beforeZoom: function(start, end) {                  // called before zoom, return false to prevent zoom
            return true;
          },
          afterZoom: function(start, end) {                   // called after zoom
          }
        }
      }
    }
  }
});
```

## Development

You first need to install node dependencies (requires [Node.js](https://nodejs.org/)):

    > npm install

The following commands will then be available from the repository root:

    > gulp build            // build dist files
    > gulp build --watch    // build and watch for changes
    > gulp lint             // perform code linting
    > gulp docs             // generate GitBook documentation (`dist/docs`)
    > gulp samples          // prepare samples for release (`dist/samples`)
    > gulp package          // create an archive with dist files and samples
    > gulp netlify          // prepare Netlify artifacts (`dist/www`)

## License

`chartjs-plugin-crosshair` is available under the [MIT license](LICENSE.md).

## Generating access token

https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token

## Deploy
Authenticating with a personal access token
You must use a personal access token with the appropriate scopes to publish and install packages in GitHub Packages. For more information, see "About GitHub Packages."

You can authenticate to GitHub Packages with npm by either editing your per-user ~/.npmrc file to include your personal access token or by logging in to npm on the command line using your username and personal access token.

To authenticate by adding your personal access token to your ~/.npmrc file, edit the ~/.npmrc file for your project to include the following line, replacing TOKEN with your personal access token. Create a new ~/.npmrc file if one doesn't exist.

//npm.pkg.github.com/:_authToken=TOKEN
To authenticate by logging in to npm, use the npm login command, replacing USERNAME with your GitHub username, TOKEN with your personal access token, and PUBLIC-EMAIL-ADDRESS with your email address.

If GitHub Packages is not your default package registry for using npm and you want to use the npm audit command, we recommend you use the --scope flag with the owner of the package when you authenticate to GitHub Packages.

$ npm login --scope=@OWNER --registry=https://npm.pkg.github.com

> Username: USERNAME
> Password: TOKEN
> Email: PUBLIC-EMAIL-ADDRESS