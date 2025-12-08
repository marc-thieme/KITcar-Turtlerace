# KITcar turtle race
This repository is part of the KITcar onboarding.
You find the instructions for what to do with the repo in the wiki.

# Prerequisite
In order to complete the turtlerace-onboarding,
you need to have your own [fork](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo)
of the repository.
For that, viewing this repo in your browser on GitHub, click on the "fork"-button in the top right
and follow the wizard.
Don't change the suggested name.
This will create the forked repository at `https://github.com/<your username>/KITcar-Turtlerace`.

# Setup
We recommend to work with the repository in combination with [kitcar-ws](https://github.com/KITcar-Team/kitcar-ws).

Here are the instructions on how to achieve this setup.

0.  Choose a directory where you want to place all of the files.
    A common place would be for example in a folder like `~/kitcar/`. If
    you don’t know what that means, read about it
    [here](<https://linuxvox.com/blog/home-in-linux/>) or ask your
    favorite LLM).

1.  At KITcar, we use the [`kitcar-ws`](https://github.com/KITcar-Team/kitcar-ws) repository for development.
    This repository contains a template for ROS development and vscode-configuration.
    More importantly, it also provides a
    [devcontainer](https://code.visualstudio.com/docs/devcontainers/create-dev-container).
    This devcontainer provides an environment where ROS 2 and all other dependencies are installed,
    facilitating development.
    To set up this devcontainer, follow the
    [readme in kitcar-ws](https://github.com/KITcar-Team/kitcar-ws/blob/main/README.md).
    You can skip the `colcon build --symlink-install` step because we don't need to build any of the standard projects.

2.  After following the instructions,
    you should have vscode open and connected to the devcontainer.
    In order to verify this, open a terminal in vscode and run the command `whoami`.
    This should output `kitcar`.
    If it outputs anything else,
    make sure that you opened the folder of the `kitcar-ws` repository
    (and neither a sub-, nor a superfolder).
    Then, you should be able to open
    the command palette (CTRL+SHIFT+P) and search for
    *Dev Containers: Open Workspace in Container*.

3.  Now, we need to run more commands in a terminal inside vscode.
    First, run `cd ~/ws/src` to enter the `src`-directory,
    where all of the repositories reside.
    Here, we want to add the turtlerace-repo as well.
    You do this by running
    ```
    git clone https://github.com/<your username>/KITcar-Turtlerace
    ```
    Replace `<your username>` with your actual GitHub username.
    This will actually clone the fork that you created of the repository.

4.  From now on, you want to run all commands inside the turtlerace folder.
    To place your terminal into that folder, run
    ```
    cd ~/ws/src/KITcar-Turtlerace
    ```
    (if you are confused about the folder your terminal is in at any point,
    you can always return to that folder by running the above command).
    Running commands like `colcon build --symlink-install` in a different folder accidentally
    won't break anything.
    It will just build unnecessary packages, so there is no need to be afraid.

5.  Now you can run `colcon build --symlink-install` to build the turtlerace packages.

6.  If it builds correctly,
    you can source the setup script for the packages by running
    ```
    source ~/ws/src/KITcar-Turtlerace/install/setup.zsh
    ```
    You need to run this command in every new terminal so later commands know
    about the packages that the turtlerace provides.

7.  If you don't want to have to run this command in each new terminal,
    you can run the following command *once*:
    ```
    echo 'source ~/ws/src/KITcar-Turtlerace/install/setup.zsh' >> ~/.zshrc
    ```
    Now, the script will be sourced in each new terminal automatically.
