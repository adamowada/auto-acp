# Auto-ACP 
#### by Adam Owada

### ❓ Tired of bland, unhelpful commit messages?
### ❓ Do you frequently forget to ACP and regret it later?
### ❓ Wish your commit graph had more commits??
### 🥳 Never fear! Auto-ACP is here! 🥳

<img src="https://lh3.googleusercontent.com/QYMYEMzAS8A8uIt-0DIfslBG6T6cT-W9mYlJXyUJ5hUd0m8kI8BCZzz89hbOO82i1uxfNyBCTJMb2XHrqXlkTC8A2yhM5LDVdhT0pBGwwR7EpNSS7ul956HWK_7TbsT__8aVmkfNcnZU6EmwarSXF1Orn6bv5eO_gPTgAmrJWjYGKNMNg8GWGJFCkwMhybzDPSXKL85jKx3M6Z53pLNvOHWXvF8X2CdnMiiqkQyyQlkjZ6T9CFguOEsQh7qHsk-htjgtw4ZsArbNP9EmIAYmoxnMmE10X2QmohbMd2XLIX53M1mpzlcng7VO104marSRl5Y1c5_rZDdsljvhJ3fmaJywsEzowBy_x6MgIK-O32p3xDYX933CRfj965fDOLURBC_OJSQ5IatgkwXXKK69JUu-NUZcvV_A7ENuyw4MmyfXv62YNEx3x-kKaSfZ-QP4PuNiakkFyJZjTTFrwmzTv2WAN1Dm17b248Dzr57Te4TvNQJcOper43WPn5emEZ-RL4Fk60jLNYlH4V3cl53wq0-08Y0kKX-kogvj1anESKshOTFs3qICKVBpPMviOWIzv6ktU1bLxKOqmfjWXNPV4Ki6C2v7FgqW7rLViq8FcZSxtvEi7oIgL5vb_9orP0l-b0eztg5pLzth7wLAKEUZjFlJvFOOV-lGrFtYCWyHFJ6d-sk3_xoNH-G6AaPlg7oeDDLdbbvuDGiiUxm-mu3pQ3eSrsAvdpw_Kot1ztN0L0OGmeNOJaPsCyxdV4-CIH5Uro7tW-5ia6YtqQ-PSEfp6p4HdIhHyr2kbnemsjZUHFOYTWe7r_nwsd6pNym3W9Gyvkm5Fin2GueashdNK_eNUWlai0VRn-nL8vBrTUyLmXIGf8gpV5WGB4Pe2VehJz4_A66g9PadlMaTA9jjGbJacH0yUzuY3qwlnjMony5veT9tcw=w1238-h503-no?authuser=0" alt="Screenshot" title="Screenshot">

## Features:
- Auto-ACP is a command-line interface application written in python that allows for quick and easy git add, commit, and pushes
- Auto-ACP uses OpenAI's ChatGPT API to automatically generate a 1 line commit message
- Once installed, simply run the command `autoacp` in your terminal. Auto-ACP will then:

    1. `git add -N .`
    2. `git diff`
    3. Generate a commit message based on the output of git diff
    4. `git add .`
    5. `git commit -m "<generated_commit_message>"`
    6. `git push`
    7. Finally, Auto-ACP will print the generated commit message to the terminal

## Prerequisites:
- git
- Python 3.10 or later, pip, and venv. [Tutorial](https://codefellows.github.io/code-401-python-guide/curriculum/prework/python-tools)
- Valid API key from [OpenAI](https://platform.openai.com/signup)

## Bash Installation Instructions: (pictures and more detail coming soon)
1. Clone this repository
    - `$ git clone git@github.com:adamowada/auto-acp.git`
    - Optionally you may download as a zip, fork the repository, or use this repository as a template
2. Create a virtual environment in the root of your directory
    - `$ cd auto-acp`
    - `$ python3.11 -m venv .venv`
    - Optionally use an older version of python (it works with 3.10.6. No guarantees)
3. Activate virtual environment
    - `$ source .venv/bin/activate`
4. Pip install requirements
    - `$ pip install -r requirements.txt`
5. Create an `.env` file in the root of your directory (same location as .env.sample)
    - `$ touch .env`
6. Edit .env following the example of `.env.sample` and of course add your own personal API key
7. Edit `autoacp` in a file editor of your choosing:
    1. Change line 1 the be the absolute path of your virtual environment's python
    2. Change line 10 to be the absolute path of your `.env` file
8. Make the `autoacp` file an executable
    - `$ chmod +x autoacp`
9. Add the root directory to your $PATH variable. The easiest way to do this is to add a line to the bottom of your .bashrc file
    - `export PATH=$PATH:/home/adam/projects/auto-acp`
    - Restart your terminal 
10. Test by running `$ autoacp` in a git repository with uncommitted changes

> **Optional Step:** Add a watch alias to your .bashrc:
- Add this to the bottom of your `.bashrc` file:
```bash
aacp() {
    wait="$*"
    watch -n $wait autoacp
}
```
- Then when you are working you can run `$ aacp 60` which will use watch to autoacp every 60 seconds (or however many seconds you pass as an argument)
 
## Known Issues:
  - Large diffs that cause the request to exceed 4096 tokens, which is approximately 16,000 characters, will fail
  - This could happen whenever many boilerplate files are created
  - Does a good job describing 'what' changes were made, but not the 'why' or 'how'
  - OpenAI's API is **paid**. Therefore while this app is free, using it will cost you **money**. Use at your own risk
 
## TODO:
  - Add pictures to installation guide
  - Make installation easier
  - Add configuration option to match commit message style guides
