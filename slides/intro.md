
# What's inside that package?

*or*

## another talk about a JSON file

---

"So, what do you think about this package?"

![](img/three-eyed-fish.jpg)

---

## If you keep asking for fish...

you'll get the same fish as everyone else

---

## Stop asking for fish

![](img/go-fishing.jpg)

---

You'll learn something and it's more fun

---

## Fishing spots

* npmjs.com/package/<package_name>
* npmjs.com/browse/keyword/<tag_name>
* node-modules.com
* npmsearch.com - LMGTFY for pacakges
* eirikb.github.io/nipster/
* libraries.io/npm

---

So you find some package... and then you eventually end up back here:

![](../img/npm-logo.svg)

---

# Things to look for on NPM

npmjs.com/package/&lt;package_name&gt;

---

## 1: Check the stats

---

![](img/npm-sidebar.png)

---

## Stability

* version number
* last published date
* publisher
* collaborators

---

## Popularity

* downloads
* open issues
* pull requests

---

## Engagement

* releases
* open issues
* pull requests

---

## Longevity

* license
* authors
* link to repo

---

## 2: Try it out

![](img/try-it-out.png)

`tonicdev.com/<github_user|org>/<repo_name>`

---

## 3: Check out the code

Either cruise the repo or install it locally...

...and the first place to look is `package.json`

---

## Know what you're getting into

`who` &amp; `what`

---

## `author`, `contributors`, `maintainers`

It can be easy to forget sometimes, but it's people who write code

You may find someone familiar--even better if you find
someone you can trust

---

## `description`

Package names don't often describe what a package actually does.
This field hopefully gives you a better clue

---

## `version`

semver 2.0 makes it much easier to reason about a package as a dependency. Ideally they follow it

Even better if they use `dist-tags` like `latest`, `beta`, `prerelease`, or `stable`

---

## `name`

A `name` like `@foo/bar` means the module `bar` is scoped to an organization `foo`

---

## `keywords`

Checking out other packages with similar tags can help give you an idea about what else is out there

---

## A quick note on npm search

Search on npmjs.com is powered by package `name`, `tags`, and `description`

But mostly just `name` and `tags`

---

## `license`

Allows us to justify use of third-party packages to lawyers if any legal issues arise

This unfortunately matters... but fortunately, many packages are published under a very liberal license

`MIT` is a good one to look for

There's a list of them here: https://spdx.org/licenses/

---

## `package.json` ~~is~~ can be a treasure map

`where`

---

## `main`

This is the primary entry point for the module

`index.js` or `index.node` will be used if `main` is omitted

Some applications will use a `start` script, but that's not
valid module syntax

---

## `repository`

You're probably already here, but in case you're not, this is where the code lives

---

## `homepage`

Many larger projects have a site of their own.

Can be a great source of docs, examples, tools, and other information.

Oddly, this field is not used on npm's module page

---

## `bugs`

The place for tracking bugs. Github is used much of the time, but sometimes not (`babel` for example)

---

## `engines`, `os`, `cpu`

Most packages are platform agnostic, so these are often left empty.  If it's important, these should be filled out

They are advisory-only, so give a module a chance if you're dealing with something outside the norm

---

## `bin`

File or files that will be symlinked into `/node_modules/.bin`

These are sourced when running npm scripts

(more on scripts later...)

---

## `man`

Files to use as man pages

Uncommon outside command-line utilities

---

## `directories`

* `directories.lib`: where the bulk of the stuff lives
* `directories.bin`: alternative to `bin`
* `directories.man`: alternative to `man`
* `directories.doc`: docs beyond `README.md`
* `directories.example`: the stuff in action

The `npm` package uses these, but I've rarely seen them other
places

---

## You can't have any pudding if you don't eat your meat

`how` the module gets stuff done

---

## `dependencies`

A list of stuff that a module needs to run

These will always be installed along with the module

`npm` advocates for small modules over frameworks, so a
long list of dependencies is not necessarily bad

A good place to find other modules worth investigating

---

## `devDependencies`

A list of stuff that a module needs for development

* included when running `npm install` inside the module folder
* not when using a module as a dependency
* not included when running `npm install --production`
* test harnesses, transpilers, and other build tools go here

---

## `peerDependencies`

Stuff compatible with the module

Commonly seen with plugin-friendly tools like `grunt`, `gulp`, `babel`, and `webpack`

* automatically installed with `npm@1-2`
* must be installed manually when `npm@3`

---

## `optionalDependencies`

Overrides modules listed in `dependencies`

Dependencies that the author would prefer to use, but that
shouldn't cause a module's installation to fail if they cannot
be included

Some examples would be os-specific modules

---

## `bundledDependencies`

Similar to `npm-shrinkwrap.json`; bundled in the tarbal created when publishing a package

Either a module listed in `dependencies` or a folder in `/node_modules` checked in to `git`

Note: http://stackoverflow.com/questions/11207638/advantages-of-bundleddependencies-over-normal-dependencies-in-npm

---

## `files`

Files and folders explicitly included when publishing a package

Alternative to `.npmignore`

---

## Config and scripts

---

## `config`

Configures environment variables for npm and a package's npm scripts

Properties added to the environment are prefixed with
`npm_config_`, but will be overridden by any existing
environment variables

`CASE_insensitive`

---

## `scripts`

`npm` is also a script runner. Examining the available scripts
in a module can reveal package features, ecosystem, and conventions

Well-curated scripts are a good sign

---

Two types of scripts:

* package lifecycle
* arbitrary

---

## Lifecycle scripts

Predetermined scripts like `test`, `version`, `publish`, and `install` that can augment the default `npm` lifecycle

Can be helpful to see how the authors manage the package

(complete list found here: https://docs.npmjs.com/misc/scripts)

---

## Arbitrary scripts

Custom scripts used by the package itself

Some common scripts I've come across include:

* `babel`
* `grunt`
* `gulp`
* `webpack`
* `dev`

---

## `scripts` cont...

Built-in hooks with `pre` and `post` prefixes work on both

Sometimes organized into smaller tasks with naming conventions like `test-unit`, `start:dev`, or `babel:watch`

Scripts can run other scripts

---

![](img/yertle-turtle.jpg)

Turtles, yo

---

## Do as I say

`npm` commands that modify `package.json`

---

## `npm install --save <package>`

Adds the latest version of a package to `dependencies`

`^` prefix will continue to pull the latest minor and patch versions in subsequent installs

---

## `npm install --save-dev <package>`

Adds the latest version of a package to `devDependencies`

---

## `npm update --save <package>`

Updates the version listed in `package.json` to the latest version that satisfies the existing semver specified

Omitting a `<package>` will update all dependencies

Also works with the `--dev` flag

Often run after `npm outdated`

---

## Never forget

`npm star` will save a package to your list of starred packages if you're logged in

`npm adduser` to log in via the `npm`

---

## Beyond the `pacakge.json`

Other signs of a quality module

* `/tests`
* `.travis.yml`
* `CHANGELOG.md`
* `.babelrc`
* `.eslintrc`
* `.editorconfig`

---

## What if there are bad signs?

* no README.md
* no `index` or `"main"`
* missing `/tests`

---

Fork, collaborate, and listen!

---

Or take what you've learned and publish something...

---

...but don't forget to tell the world.

---

## Go fish!
