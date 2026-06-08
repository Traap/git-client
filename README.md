### Git-Client
This repository validates the Git command line client as a software lifecycle
tool.  The validation is automated by
[amber](https://github.com/traap/amber), documented with
[autodoc](https://github.com/traap/autodoc), built with
[docbld](https://github.com/traap/docbld), and exercised against the
[QuickSort](https://github.com/traap/quicksort) product repository.

Each `~/soup` folder is treated as a complete product checkout.  `git-client`
uses the local `~/soup/quicksort` repository to prepare a temporary bare Git
remote under `remote/quicksort.git` inside the current `git-client` checkout;
Amber then validates Git CLI behavior by cloning, branching, committing,
pushing, merging, reverting, and tagging against that local remote.

### Supported Systems
**git-client** targets Linux-like shells with Ruby, Git, Amber, Autodoc, docbld,
and tlc-article available.

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
1. Meet all prerequisites.
2. Ensure `AMBERPATH`, `AUTODOCPATH`, and `DOCBLDPATH` are defined.
3. Ensure `~/soup/quicksort` is present.
4. Move to `~/soup/git-client`.
5. Run the validation task.

```bash
cd ~/soup/git-client
rake validate:git
```

The validation task fails if required environment variables are missing, if the
local QuickSort product checkout is unavailable, if Amber returns a non-zero
status, or if docbld cannot build and deploy the report.

### Review the git-client.pdf
Report moved to **_build/git-client.pdf**
