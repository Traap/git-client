### WebDriver 
This repository is used to validate Git client tool
in accordance FDA Quality Systems Regulation 820.70(i) Automated Processes.

### Supported Systems
**git-client** has been tested with cygwin, linix, linux (mint), mingw32,
and wsl.

### Prerequisites
#### Applications
1. [git client](https://git-scm.com/book/en/v2/Git-and-Other-Systems-Git-as-a-Client)
2. [Ruby](https://www.ruby-lang.org/en/downloads/)
3. [Rake](https://ruby.github.io/rake/)
4. [Bundler](https://bundler.io) 

#### Clone Repositories 
1. [amber](https://github.com/Traap/amber)
2. [autodoc](https://github.com/Traap/autodoc) 
3. [docbld](https://github.com/Traap/docbld) 
4. [tlc-article](https://github.com/Traap/tlc-article) 
5. [CoreWebApp](https://bitbucket-vial.intra.fresenius.com/scm/rdtest/corewebapp
6. [QuickSort](https://bitbucket-vial.intra.fresenius.com/scm/san/quicksort)

### Validating Git Command Line Client
1. Meet all perquisites
2. Create shell
3. Move to $HOME/git/git-client
4. Run [amber](https://github.com/Traap/amber)

```bash
cd $HOME/git/git-client

amber --verbose --nodryrun --writer=LaTeX --plan=command-line

docbld
```

### Review the git-client-validation.pdf
Report moved to **_build/git-client-validation.pdf**
