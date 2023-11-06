<div align=center>

![Website](https://img.shields.io/website?up_message=AVAILABLE&down_message=DOWN&url=https%3A%2F%2Fclickhouse.com%2Fdocs&style=for-the-badge)
[![CC BY-NC-SA 4.0 License](https://img.shields.io/badge/license-CC-blueviolet?style=for-the-badge)](http://creativecommons.org/licenses/by-nc-sa/4.0/)
![Checks](https://img.shields.io/github/actions/workflow/status/clickhouse/clickhouse-docs/debug.yml?style=for-the-badge&label=Checks)

<picture align=center>
    <source media="(prefers-color-scheme: dark)" srcset="https://github.com/ClickHouse/clickhouse-docs/assets/9611008/4ef9c104-2d3f-4646-b186-507358d2fe28">
    <source media="(prefers-color-scheme: light)" srcset="https://github.com/ClickHouse/clickhouse-docs/assets/9611008/b001dc7b-5a45-4dcd-9275-e03beb7f9177">
    <img alt="The ClickHouse company logo." src="https://github.com/ClickHouse/clickhouse-docs/assets/9611008/b001dc7b-5a45-4dcd-9275-e03beb7f9177">
</picture>

<h4>ClickHouse® is an open-source column-oriented database management system that allows generating analytical data reports in real-time.</h4>

</div>

---

ClickHouse is blazing fast, but understanding ClickHouse and using it effectively is a journey. The documentation is your source for gaining the knowledge you need to be successful with your ClickHouse projects and applications. [Head over to clickhouse.com/docs to learn more →](https://clickhouse.com/)

## Table of contents

- [About this repo](#about-this-repo)
- [Run locally](#run-locally)
- [Contributing](#contributing)
- [Issues](#issues)
- [License](#license)

## About this repo

This repository manages the documentation for [ClickHouse](https://clickhouse.com/docs). The content is built with [Docusaurus](https://docusaurus.io/) and hosted on [Vercel](https://vercel.com). Documentation content is written in Markdown and is held in the `/docs` directory.

## Run locally

You can run a copy of this website locally within a few steps. Some folks find this useful when contributing so they can see precisely what their changes will look like on the production site.

1. Install Git, NPM, and Yarn. If you already have them installed, skip this step:

    | OS | Package manager | Install command | 
    | ---| --------------- | --------------- |
    | MacOS | Homebrew | `brew install git node yarn` |
    | Ubuntu | Apt | `sudo apt install git nodejs npm yarn` |
    | Arch | Pacman | `sudo pacman -S git nodejs npm yarn` |
    | Windows | Chocolatey | `choco install git nodejs-lts yarn` |

1. Clone this repository and move into the `clickhouse-docs` directory:

    ```shell
    git clone https://github.com/clickhouse/clickhouse-docs
    cd clickhouse-docs
    ```

1. Install the project dependencies with Yarn:

    ```shell
    yarn install

    # yarn install v1.22.19
    # [1/5] 🔍  Validating package.json...
    # [2/5] 🔍  Resolving packages...
    # ...
    # success Saved lockfile.
    # ✨  Done in 6.44s.
    ```

1. Use Yarn to grab the latest documentation changes from the `clickhouse/clickhouse` repository:

    ```shell
    yarn prep-from-master

    # yarn run v1.22.19
    # Cloning into '/tmp/ch_temp_14714'...
    # ...
    # Prep completed
    # ✨  Done in 16.44s
    ```

1. Start the local web-server:

    ```shell
    yarn start

    # yarn run v1.22.19
    # $ docusaurus start
    # ...
    #
    ```

    This command will build the documentation site and serve it locally. Once the build has finished, browse the website at [localhost:3000](http://localhost:3000/docs/en/intro).

1. To stop the local server, press `ctrl` + `c` in the terminal window.

If you want to build a static copy of this repository that doesn't require a constant server running to view, you can use `yarn build` instead of `yarn start`. The `yarn build` will output a static copy of the website in the `/build` directory. This process takes around 10 minutes to complete on an M1 Macbook with 8GB RAM.

### Notes

Here are some things to keep in mind when building a local copy of the ClickHouse docs site.

#### Build-time

Due to the complex structure of this repo, the docs site can take some time to build locally. As a benchmark, it takes ~3 minutes to build on an M1 Macbook with 8GB RAM.

#### Redirects

Due to how the local server is built, redirects will not work. For example, visiting `clickhouse.com/docs` on the production site will lead you to `clickhouse.com/docs/en/intro`. However, on a local copy of the site, you will see a 404 page if you try to visit `localhost:8000/docs`.

## Contributing

Want to help out? Contributions are always welcome! If you want to help out but aren't sure where to start, check out the [issues board](https://github.com/clickhouse/clickhouse-docs/issues).

### Pull requests

Please assign any pull request (PR) against an issue; this helps the docs team track who is working on what and what each PR is meant to address. If there isn't an issue for the specific _thing_ you want to work on, quickly create one and assign yourself to it.

Check out the GitHub docs for a refresher on [how to create a pull request](https://docs.github.com/en/desktop/working-with-your-remote-repository-on-github-or-github-enterprise/creating-an-issue-or-pull-request-from-github-desktop).

### Tests and CI/CD

There are five workflows that run against PRs in this repo:

| Name | Description |
| ---- | ----------- |
| [Debug](https://github.com/ClickHouse/clickhouse-docs/blob/main/.github/workflows/debug.yml) | A debugging tool that prints environment variables and the content of the `GITHUB_EVENT_PATH` variable for each commit. |
| [Link check](https://github.com/ClickHouse/clickhouse-docs/blob/main/.github/workflows/linkcheck.yml) | Checks for broken external links in this repo. |
| [Pull request](https://github.com/ClickHouse/clickhouse-docs/blob/main/.github/workflows/pull-request.yml) | This is a _meta_ workflow that sets up a testing environment and calls the `docs_check.py` and `finish_check.py` scripts. |
| [Scheduled Vercel build](https://github.com/ClickHouse/clickhouse-docs/blob/main/.github/workflows/scheduled-vercel-build.yml) | Builds the site every day at 00:10 UTC and hosts the build on Vercel. |
| [Trigger build](https://github.com/ClickHouse/clickhouse-docs/blob/main/.github/workflows/trigger-build.yml) | Uses the [peter-evans/repository-dispatch@v2](https://github.com/peter-evans/repository-dispatch) workflow to create a repository dispatch. |

## Issues

Found a problem with the Clickhouse docs site? [Please raise an issue](https://github.com/clickhouse/clickhouse-docs/issues/new). Be as specific and descriptive as possible; screenshots help!

## License

This work is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/).
