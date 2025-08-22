# Pokengine Readthedocs

This repository contains the official Readthedocs documentation for the Pokengine project.

-----

## About This Project

This documentation serves as a central hub for the **jCoad Coding Language** and **MapBuilder**, which is the proprietary event editor for Pokengine. The documentation uses the **Material for Mkdocs** theme. You can find more information about this theme, including requirements and coding, at **mkdocs-material**.

-----

## Contributing 

This repository is primarily for documentation, so contributions should focus on improving or adding to the existing content. 

The standard GitHub workflow for contributing through Github Web is:

1.  **Fork the Repository:** Create a copy of the Pokengine repository on your own GitHub account.
2.  **Clone Your Fork:** Clone your new repository to your local machine using the command:
    ```
    git clone https://github.com/YOUR-USERNAME/Pokengine.git
    ```
    (Remember to replace `YOUR-USERNAME` with your actual GitHub username.)
3.  **Make and Commit Your Changes:** Navigate into the directory and make your changes. Once done, stage and commit them:
    ```
    cd Pokengine
    git add .
    git commit -m "A brief, descriptive message about your changes"
    ```
4.  **Push Your Changes:** Push your committed changes to your remote repository on GitHub:
    ```
    git push origin main
    ```
5.  **Create a Pull Request (PR):** Go to your forked repository on GitHub and click the **Compare & pull request** button. Provide a clear title and detailed description for your changes, then click **Create pull request** to submit it for review by the project maintainers.

Of course! Here’s how you can use **GitHub Desktop** to contribute to a repository, formatted in markdown.

### **Contributing with GitHub Desktop**

Using **GitHub Desktop** simplifies the contribution process by providing a visual interface for many of the actions you would normally perform on the command line.

---

### 1. Fork the Repository

First, you still need to fork the repository on the GitHub website. Navigate to the main Pokengine repository page and click the **Fork** button in the top-right corner. This creates a copy of the repository under your own GitHub account.

---

### 2. Clone Your Fork

Open the **GitHub Desktop** application.

* Click **File > Clone repository** from the menu.
* You'll see a list of your repositories. Select the Pokengine fork you just created.
* Choose a local path on your computer where you want to store the project files.
* Click **Clone** to download the repository to your machine.

---

### 3. Make and Commit Your Changes

* After cloning, you can access the local repository folder directly from GitHub Desktop by clicking **Show in Explorer** (on Windows) or **Show in Finder** (on macOS).
* Make your desired changes to the documentation files.
* As you save your changes, GitHub Desktop will automatically detect them. The application's left-hand panel will show a list of all the files you've modified.
* Check the boxes next to the files you want to include in your commit.
* At the bottom of the left panel, write a brief, descriptive **commit summary** and an optional extended description.
* Click the **Commit to main** button.

---

### 4. Push Your Changes

* After committing, a **Push origin** button will appear at the top of the application window.
* Click this button to upload your committed changes from your local computer to your forked repository on GitHub.

---

### 5. Create a Pull Request (PR)

* Once you have successfully pushed your changes, a new button labeled **Create Pull Request** will appear at the top of the GitHub Desktop window.
* Clicking this button will open your web browser and take you directly to the pull request creation page on the original Pokengine repository.
* The page will be pre-filled with the necessary information. Provide a clear title and a detailed description of your changes, then click **Create pull request**.

The project maintainers will then review your contribution and decide whether to merge it into the main project.

-----

## Building to Readthedocs
If there is any additional problem with rebuilding the documentation, here are the instructions on how to build on readthedocs.
To build your project documentation on Read the Docs, you need to follow these steps:

1.  **Prepare Your Project:** Your documentation should be in a `docs` folder at the root of your repository. Pokengine documentation is written in **Markdown (.md)**. The `docs` folder should include an `index.md` file and a `conf.py` file for **Sphinx** configuration. If your documentation requires any Python libraries, include a `requirements.txt` file in the `docs` directory.
2.  **Sign Up and Connect:** Sign up for an account on the [Read the Docs website](https://readthedocs.org/). Connect your version control provider (e.g., GitHub) to grant it access to your repositories.
3.  **Import Your Project:** From your Read the Docs dashboard, click **Import a Project**. Select your repository from the list and click **Build**.
4.  **Configure the Build:** Create a `.readthedocs.yaml` file in your project's root directory to customize the build process. This file lets you specify the Python version, your `requirements.txt` location, and other build settings. Here is an example:
    ```yaml
    # .readthedocs.yaml
    # Read the Docs configuration file
    # See https://docs.readthedocs.io/en/stable/config-file/v2.html for details

    # Required to use the new v2 config
    version: 2

    # Set the version of Python
    build:
      os: ubuntu-22.04
      tools:
        python: "3.10"

    # Build documentation in the docs/ directory with Sphinx
    sphinx:
      configuration: docs/conf.py

    # Install any required dependencies
    python:
      install:
      - requirements: docs/requirements.txt
    ```
5.  **Monitor the Build:** You can monitor the build status from your Read the Docs project page. Once a build is successful, your documentation will be live at a URL like `https://<project-name>.readthedocs.io/en/latest/`. Any new pushes to your `main` branch will automatically trigger a new build.

-----

## License

This code and language are **not to be used for any purpose other than Pokengine**.

-----

## Credits

  * Documentation is managed by the Admin, Moderation, and Development staff at **pokengine.org**.
  * Original documentation and inspiration by **Zermonious**.
  * New Readthedocs setup created by **PixelMister**.
