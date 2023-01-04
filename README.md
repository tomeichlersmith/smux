# NAME

smux v1.0.1

# SYNOPSIS

**smux** [SSH Options] [\-\-help] [\-\-list] destination [session]

# DESCRIPTION

**smux** is a light, POSIX-compliant wrapper around ssh and tmux, allowing the user to directly attach to remote tmux sessions with one command.

## OPTIONS

**SSH Options** all single-dash options are provided to the ssh command

**\-\-help**      show the help message and exit

**\-\-list**      list the tmux sessions on the given destination rather than trying to connect

## ARGUMENTS

**destination**     remote host to connect to via ssh

**session**         name of tmux session on the given host to attach to (or create if it doesn't exist)

# EXAMPLES

Most simply, use as a drop in replacement for ssh. Instead of exiting, detach from your tmux session on the remote, and then you can always resume what you were doing after needing to leave the ssh connection.

    smux destination

One benefit of tmux is that it can host many sessions on the same machine at once, each of which have a unique name to identify it. 

    smux destination session

Want to see what tmux sessions are already created on a specific remote, you can use the list option.

    smux --list destination

# INSTALLATION

## curl

If you trust me (or have proofread the install script), you can install smux with a one-liner.

    curl -s https://raw.githubusercontent.com/tomeichlersmith/smux/main/install | sh 

By default, this installs smux to ~/.local if you are a non-root user.
You can define the install prefix (--prefix dir) and 
choose to use the HEAD of the main branch rather
than the last release (--next) both of which are optional.

    curl -s https://raw.githubusercontent.com/tomeichlersmith/smux/main/install | \
      sh -s -- --prefix dir --next

## git

You can install or update smux by obtaining the source code from the repository https://github.com/tomeichlersmith/smux either by cloning it or by downloading one of the releases and then running the installation command.

    cd smux
    ./install

# CONTRIBUTING

Feel free to create a fork of https://github.com/tomeichlersmith/smux and open a Pull Request with any bug patches or feature improvements. We aim to keep smux as a single file with optional completion and manual files in parallel. Check that smux is still POSIX with dash.

    dash -n smux

Install shellcheck from https://github.com/koalaman/shellcheck and use it to make sure smux avoids common shell scripting errors.

    shellcheck -s sh -a -o all -Sstyle -Calways -x smux
