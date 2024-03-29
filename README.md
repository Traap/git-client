### Git-Client
This repository is used to validate the Git client tool in accordance with FDA
Quality Systems Regulation 820.70(i) Automated Processes.

### Supported Systems
**git-client** has been tested with cygwin, linix, mingw32, and wsl.

### Prerequisites
#### Applications
1. [git client](https://git-scm.com/book/en/v2/Git-and-Other-Systems-Git-as-a-Client)
2. [Ruby](https://www.ruby-lang.org/en/downloads/)
3. [Rake](https://ruby.github.io/rake/)
4. [Bundler](https://bundler.io)

#### Clone Repositories
1. [amber](https://github.com/traap/amber)
2. [autodoc](https://github.com/traap/autodoc)
3. [docbld](https://github.com/traap/docbld)
4. [tlc-article](https://github.com/traap/tlc-article)
5. [QuickSort](https://github.com/traap/quicksort)

### Validating Git Command Line Client
1. Meet all perquisites
2. Create shell
3. Move to $HOME/git/git-client
4. Run [amber](https://github.com/traap/amber.git)

```bash
cd $HOME/git/git-client
```

```bash
rake validate:git
```

### Review the git-client.pdf
Report moved to **_build/git-client.pdf**
