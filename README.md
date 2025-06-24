# go-ai-agent

This repo contains the code for Thorsten Ball's "How to Build an Agent" post
(see [here](https://ampcode.com/how-to-build-an-agent)).

## Setup

This repo contains everything you need to get a development environment ready
to go through the tutorial. You'll first need to make sure `nix` and `direnv`
are installed. An anthropic API key is also required (one can be generated
[here](https://console.anthropic.com/)).

### Install Nix

Nix is package manager that allows us to "make reproducible, declarative and
reliable systems" (according to [their site](https://nixos.org/)).

Nix can be installed using [the Determinate Systems
installer](https://github.com/DeterminateSystems/nix-installer). Run the
following command:

```bash
curl -fsSL https://install.determinate.systems/nix | sh -s -- install --determinate
```

### Install Direnv

[Direnv](https://direnv.net/) is a tool that enables us to quickly load and
unload an environemnt when we enter and leave a directory.

Direnv is available in homebrew. Run the following command:

```bash
brew install direnv
```

Once it's installed you'll have to configure your shell. If you're using ZSH
run the following:

```bash
echo 'eval "$(direnv hook zsh)"' >> ~/.zshrc
```

NOTE: You'll have to start a new terminal session for the changes in `~/.zshrc`
to take effect!

For all other shells, refer [here](https://direnv.net/docs/hook.html).

### Configure Anthropic API Key

First, generate an Anthropic API key from [the
console](https://console.anthropic.com/). This repo has a `.envrc` (direnv
configuration file) that will read from a `.env` file (not committed to this
repo since we'll use it to house secrets). Once you have your API key, run the
following (make sure to replace the placeholder text with your actual API key):

```bash
echo 'export ANTHROPIC_API_KEY=<your generated key>' > .env
```

### Build the Development Environment

We're now ready to build the development environment. Direnv configuration
files (`.envrc` files) have to be explicitly trusted before they take effect.
Run the following to build and automatically enter the development environment:

```bash
direnv allow
```

Once that runs, nix will do its thing and set up the environment. This might
take a bit. Once it's done you can check to see if it worked by running the following:

```bash
which go
```

This should spit out a value like
`/nix/store/fd2s1z3why92qn8w7j6r0xlarikpv27v-go-1.24.2/bin/go`.

## Follow the Tutorial

You can now follow [the tutorial](https://ampcode.com/how-to-build-an-agent).
This repo also has some branches containing the tutorial code as well if you'd
prefer to not copy/paste (or preferably type it out) yourself. Branches
`step1`, `step2`, `step3`, `step4` correspond to the different parts of the
tutorial. `step1` is the initial setup of the conversation loop and the other
steps correspond to the three tools you'll implement as part of the tutorial.
