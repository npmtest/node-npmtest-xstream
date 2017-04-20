# npmtest-xstream

#### basic test coverage for  [xstream (v10.5.0)](https://github.com/staltz/xstream#readme)  [![npm package](https://img.shields.io/npm/v/npmtest-xstream.svg?style=flat-square)](https://www.npmjs.org/package/npmtest-xstream) [![travis-ci.org build-status](https://api.travis-ci.org/npmtest/node-npmtest-xstream.svg)](https://travis-ci.org/npmtest/node-npmtest-xstream)

#### An extremely intuitive, small, and fast functional reactive stream library for JavaScript

[![NPM](https://nodei.co/npm/xstream.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/xstream)

| git-branch : | [alpha](https://github.com/npmtest/node-npmtest-xstream/tree/alpha)|
|--:|:--|
| coverage : | [![istanbul-coverage](https://npmtest.github.io/node-npmtest-xstream/build/coverage.badge.svg)](https://npmtest.github.io/node-npmtest-xstream/build/coverage.html/index.html)|
| test-report : | [![test-report](https://npmtest.github.io/node-npmtest-xstream/build/test-report.badge.svg)](https://npmtest.github.io/node-npmtest-xstream/build/test-report.html)|
| build-artifacts : | [![build-artifacts](https://npmtest.github.io/node-npmtest-xstream/glyphicons_144_folder_open.png)](https://github.com/npmtest/node-npmtest-xstream/tree/gh-pages/build)|

- [https://npmtest.github.io/node-npmtest-xstream/build/coverage.html/index.html](https://npmtest.github.io/node-npmtest-xstream/build/coverage.html/index.html)

[![istanbul-coverage](https://npmtest.github.io/node-npmtest-xstream/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fcoverage.lib.html.png)](https://npmtest.github.io/node-npmtest-xstream/build/coverage.html/index.html)

- [https://npmtest.github.io/node-npmtest-xstream/build/test-report.html](https://npmtest.github.io/node-npmtest-xstream/build/test-report.html)

[![test-report](https://npmtest.github.io/node-npmtest-xstream/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Ftest-report.html.png)](https://npmtest.github.io/node-npmtest-xstream/build/test-report.html)

- [https://npmdoc.github.io/node-npmdoc-xstream/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-xstream/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-xstream/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-xstream/build/apidoc.html)

![npmPackageListing](https://npmtest.github.io/node-npmtest-xstream/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmtest.github.io/node-npmtest-xstream/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "name": "xstream",
    "version": "10.5.0",
    "description": "An extremely intuitive, small, and fast functional reactive stream library for JavaScript",
    "main": "index.js",
    "typings": "index.d.ts",
    "scripts": {
        "commit": "git-cz",
        "changelog": "conventional-changelog --infile CHANGELOG.md --same-file --release-count 0 --preset angular",
        "lint": "tslint -c tslint.json src/**/*.ts src/extra/*.ts",
        "premocha": "npm run compile",
        "mocha": "mocha tests/*.ts tests/**/*.ts --require ts-node/register",
        "test": "npm run lint && npm run mocha && npm run doctest",
        "doctest": "markdown-doctest",
        "setup-browser-tests": "browserify browser-tests/index.ts -p [ tsify ] > browser-tests/tests-bundle.js",
        "teardown-browser-tests": "rm browser-tests/tests-bundle.js",
        "compile": "tsc",
        "page-content": "npm run compile && rm -rf .ignore/ && mkdirp .ignore/ && npm run changelog && node tools/make-toc.js && node tools/make-factories.js && node tools/make-methods.js && cat markdown/header.md markdown/generated-toc.md markdown/overview.md markdown/generated-factories.md markdown/generated-methods.md markdown/footer.md > .ignore/content.md",
        "extra-docs": "node tools/make-extras.js && rm EXTRA_DOCS.md && cp markdown/generated-extras.md EXTRA_DOCS.md",
        "readme": "npm run page-content && cat markdown/readme-title.md .ignore/content.md > README.md",
        "postreadme": "npm run extra-docs",
        "predist": "rm -rf dist/ && mkdirp dist/ && npm run compile",
        "dist": "browserify index.js --standalone xstream | node tools/strip-comments.js > dist/xstream.js",
        "postdist": "node tools/minify.js",
        "start": "npm install && npm prune",
        "check-release": "node tools/check-release.js",
        "prepublish": "npm run compile",
        "preversion": "npm run readme && npm test",
        "version": "npm run readme && npm run dist && git add -A",
        "postversion": "git push origin master && git push origin --tags && npm publish && npm run update-gh-pages",
        "update-gh-pages": "git checkout gh-pages && rm _includes/content.md && cp .ignore/content.md _includes/ && git add --all && if git diff --cached --quiet > /dev/null; then :; else git commit -m \"update site\"; fi && git push origin gh-pages && git checkout master",
        "release": "./tools/release-if-necessary.sh",
        "release-patch": "false",
        "release-minor": "npm version minor -m \"chore(package): release new version\"",
        "release-major": "npm version major -m \"chore(package): release new version\""
    },
    "repository": {
        "type": "git",
        "url": "git+https://github.com/staltz/xstream.git"
    },
    "author": "Andre Staltz <andre+npm@staltz.com> (http://andre.staltz.com/)",
    "license": "MIT",
    "bugs": {
        "url": "https://github.com/staltz/xstream/issues"
    },
    "homepage": "https://github.com/staltz/xstream#readme",
    "dependencies": {
        "symbol-observable": "^1.0.2"
    },
    "devDependencies": {
        "@types/mocha": "^2.2.40",
        "@types/node": "^7.0.12",
        "@types/sinon": "^2.1.2",
        "assert": "1.3.x",
        "browserify": "13.0.x",
        "commitizen": "2.9.x",
        "conventional-changelog": "1.1.x",
        "conventional-changelog-cli": "1.2.x",
        "cz-conventional-changelog": "1.2.x",
        "es6-promise": "4.0.5",
        "google-closure-compiler-js": "^20161201.0.0",
        "markdown-doctest": "0.9.1",
        "markdox": "0.1.10",
        "mkdirp": "0.5.1",
        "mocha": "2.4.5",
        "most": "1.0.3",
        "sinon": "1.16.0",
        "strip-comments": "0.4.4",
        "ts-node": "1.7.2",
        "tsify": "2.0.3",
        "tslint": "4.0.2",
        "typescript": "2.1.5",
        "validate-commit-msg": "2.4.x"
    },
    "publishConfig": {
        "access": "public"
    },
    "config": {
        "commitizen": {
            "path": "./node_modules/cz-conventional-changelog"
        }
    }
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
