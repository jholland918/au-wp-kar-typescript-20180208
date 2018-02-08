# au-wp-kar-typescript-20180208
## Install
`>au new`

Project Configuration

    Name: au-wp-kar-typescript-20180208
    Platform: Web
    Bundler: Webpack
    Loader: None
    Transpiler: TypeScript
    Markup Processor: None
    CSS Processor: None
    Unit Test Runner: Karma
    Integration Test Runner: None
    Editor: Visual Studio Code

`>yarn add jest-matchers --dev`

`>yarn add karma-sourcemap-loader --dev`

### Configure tsconfig.json
Add `"sourceMap": true`

### Configure karma.conf.js
Add `mime: { 'text/x-typescript': ['ts', 'tsx'] },` to make Chrome happy

Change webpack **coverage** parameter to **false** because for some reason the sourcemaps no longer work when istanbul-instrumenter-loader is used.

`webpack: require('../webpack.config')({ coverage: false }),`

### Configure webpack.config.js
Add the following to plugins:

    new webpack.SourceMapDevToolPlugin({
      filename: null, // if no value is provided the sourcemap is inlined
      test: /\.(ts|js)($|\?)/i, // process .js and .ts files only
      exclude: [/node_modules/]
    })

