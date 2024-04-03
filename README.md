# ICS 46

Welcome to the ICS 46 GitHub landing page! This GitHub repository contains the homework setup material you need for this course. This `main` branch helps you set up the GitHub connections you need, and introduces the tools we use in this course.

While following these instructions here in this `main` branch README, you will complete the following steps:

 1. On GitHub, create an account.
 2. On Openlab and GitHub, set up SSH keys for communicating between your Openlab and GitHub accounts.
 3. On GitHub Classroom, create your own private repository.
 4. On Openlab, **clone** your repository to your Openlab.

## 1 GitHub Account

GitHub is an online storage service for the tool `git`, an industry standard version control tool with many powerful capabilities. For this course, `git` allows you to
- easily obtain files needed for each Homework from the public ICS46 course repository,
- save your work in your own account on GitHub.com (in different versions/branches if you choose, so that you can try different approaches or changes without breaking what you were working on before), and
- easily upload your Homework submissions to GradeScope directly from GitHub.

This class **requires** the use of a GitHub account, so first create your account at  [GitHub.com](https://github.com/). If you already have a GitHub account, you can use your existing account for this course. Your GitHub account does not need to be linked to your UCI email.

## 2 Configure your `git` profile and add SSH keys

On Openlab, `git` is pre-installed, so now we will set up your basic `git` profile and add your GitHub `ssh-keys` to your account! SSH keys allow secure communication between your Openlab and your GitHub accounts, without the need to log in every time.

### Configure `git` profile

Log into Openlab, as you learned to do in [HW0.1](https://sites.google.com/view/ics-46-data-structures/homework-0-1-openlab). Once logged in to your Openlab terminal, you can now type commands to `git`. 

#### :warning: Where am I? 
>***When using a terminal, always be aware of your current working directory, and whether your current directory is your **local** machine (i.e., on the hard drive of your own computer) or remote, on Openlab. When following these instructions, make sure you are logged into Openlab!***

In your Openlab terminal, add your GitHub `username` and `email` by typing the following commands. The commands below shown as `<Example>` should be replaced with **your** information:

```bash
git config --global user.name "<YourGitHubNameHere>"    # Example: "Ray Klefstad"
git config --global user.email "<YourGitHubEmailHere>"  # Example: "klefstad@uci.edu"
```
### Set up an SSH key

Now set up an `ssh` key, because `GitHub` is moving away from allowing the usage of `https` links.  

First, generate an SSH key pair for GitHub on Openlab through the following steps:

- [ ] Type or copy the following command, using your GitHub email:
```shell
ssh-keygen -t ed25519 -C "<YourGitHubEmailHere>"
```
When you're prompted to `Enter a file in which to save the key`,  press **`Enter`** to accept the default file location.

- [ ] At the next prompt, you can enter a passphrase to protect your SSH key, or simply hit **`Enter`** (twice) for no passphrase.
    
 ``` bash
$ Enter passphrase (empty for no passphrase): [Type a passphrase]
$ Enter same passphrase again: [Type passphrase again]
```

Now that you have created your SSH key on Openlab, add it to **your** `GitHub` account as follows:

- [ ] Copy the SSH public key to your clipboard:
     ```bash
      $ cat ~/.ssh/id_ed25519.pub
     ```
     Then select and copy the contents of the `id_ed25519.pub` file displayed in the terminal to your clipboard.
- [ ] On **your account** at GitHub.com, in the upper-right corner of any page, click your profile photo, then click **Settings**.
- [ ] In the left sidebar menu, click  **SSH and GPG keys**.
- [ ] Click  **New SSH key**  or  **Add SSH key**.
- [ ] In the **Title** field, add the informative label `Openlab`.
- [ ] For the type of key, make sure **Authentication** is selected.
- [ ] In the **Key** field, paste your public key.
- [ ] Click  **Add SSH key**.

## 3 Make your own private repository

Now that you have set up your `username`, `email`, and `ssh` key, navigate back to the Canvas page, and click the GitHub Classroom link. That link will automatically generate a private copy of this repository for you! (NOTE: It will ask you to authorize GitHub Classroom to have access toy our GitHub account, and you should confirm this authorization). Once you have created that repository, you can continue on to the `Clone` instructions below.

## 4 Clone this repository

Now that you have a private copy of the repository, [clone](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository) this ICS46 repository to your Openlab. On Openlab, you can clone a GitHub repository by using the command `git clone` and copy-pasting the **SSH link** you get when clicking the green `Code` button. Example below:

![](docs/clone_link.png)

So run the following command:

```bash
# This is an example ssh link, make sure to use your own!
# NOTE: the `ICS46` following the .git address indicates what folder to
# name the project you are cloning.
git clone git@github.com:klefstad-teaching/ics46-<StudentName>.git ICS46
```

At the prompt `Are you sure you want to continue connecting (yes/no/[fingerprint])?` type `yes`.

This `git clone ...` command initializes a new git repository on your Openlab and populates it with the contents of the private `ICS46` repository, adding the directory `ICS46` to your current working directory, which you can see by typing the `ls` command.

The `git clone` command also establishes the private course repository at `ICS46` as a `remote` connection called `origin`. `origin` is an alias (short nickname) for `git@github.com:klefstad-teaching/ics46-<StudentName>.git` so that you don't have to type that long connection path every time. You can then  `checkout` files from `origin`for all the future Homeworks (from the different branches named `hw0`, `hw1`...)---but **only after they are announced as available on Ed**!

With this complete, you can switch to the `HW0` branch to start on homework 0.2!

## Tools

The following are a list of tools that will be used in this course. All of these tools have been set up for use on Openlab. Remember that we **WILL NOT** be able to support issues encountered if you use your personal setup, only the setup on Openlab.

- `git`
- `gcc`
- `make`
- `cmake`
- `valgrind`
- `gtest`

### `CMake`

For this course, we use `CMake`, an industry standard for building C/C++ projects. `CMake` in this course will consist of two files provided for each homework: `CMakePresets.json` and `CMakeLists.txt`. 
- `CMakePresets.json` describes to `CMake` the arguments, flags, and preferences that you want the compiler to use when building your project, as well as telling `CMake` where to put the files that it builds (which in this course will be the `build/` folder). 
- `CMakeLists.txt` describes the `.cpp` and `.hpp` files you intend to compile, where to find them, and how to package them into an executable `target`.

Learning about `CMake` is useful to you if you ever work with C/C++ code bases. For this class, we will provide simple `CMakeLists.txt` files with annotation to explain what each part is doing, but you will not be required to change it in any way. If you are interested in learning more about `CMake`, you can find more information at the official [CMake tutorial](https://cmake.org/cmake/help/latest/guide/tutorial/index.html).

### `GTest`

Testing your programs before submitting them is **essential** and will be **required** in several Homeworks to ensure your code behaves as you expect it to. GTest is an incredibly popular testing platform for `.cpp`, especially in large code bases, and is available on Openlab.  We will cover the basics of using `GTest` and adding your own tests in the required homeworks, but for more detailed information take a look at their [primer documentation](https://google.github.io/googletest/primer.html).

## Next steps: hw0

Next, at the upper left of this page, select the `hw0` branch, and follow the instructions in the README there.

![](docs/branches.png)

To access instructions and files for all **future** Homeworks, use that same branch drop down menu at the top of this page (the public ICS46 GitHub) to select the Homework you wish to work on, **but ONLY AFTER they are announced as available on Ed**.Then follow the instructions on the README for that homework branch.

**:warning: DO NOT checkout anything from the public GitHub `ICS46` repository until its availability is announced on Ed! You may obtain out-of-date files and instructions which will confuse you, waste time, and require more advanced and complex `git` operations to undo!**
