# How to work on this website

This is a Quartz website. Here's how you can continue working on it.

## Running the development server

To see a live preview of your website, you can run the development server. The command for this is defined in the `package.json` file.

Based on the `scripts` section in `package.json`, you can run the development server with the following command:

```bash
npx quartz build --serve -d docs
```

This will build the website from the files in the `docs` directory and serve it on a local port. The server will automatically reload when you make changes to the files.

If that command is disallowed, you can try:
```bash
npm run docs
```

## Project Structure

The main content of your website is in the `docs` directory. This is specified by the `-d docs` flag in the run command.

*   `docs/`: This directory contains all your Markdown files that will be converted into web pages.
    *   `docs/index.md`: This is the homepage of your website.
    *   You can create subdirectories to organize your files.
*   `quartz.config.ts`: This file contains the configuration for your Quartz website. You can customize the theme, plugins, and other settings here.
*   `quartz.layout.ts`: This file defines the layout of your website, like the header, footer, and sidebars.
*   `package.json`: This file lists the project's dependencies and defines scripts for running and building the website.

## Building for production

When you are ready to deploy your website, you can build the static files with the following command:

```bash
npx quartz build -d docs
```

This will create a `public` directory with all the static files for your website. You can then upload this directory to any static web hosting service.
