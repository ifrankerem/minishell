<div align="center">

# 🐚 minishell

**A small UNIX-like shell in C — pipes, redirections, signals and the whole variable-environment dance.**

![Language](https://img.shields.io/badge/language-C-00599C?style=flat-square)
![42](https://img.shields.io/badge/42-Common%20Core-000000?style=flat-square)
![Readline](https://img.shields.io/badge/GNU%20Readline-42BB6B?style=flat-square)
![Norminette](https://img.shields.io/badge/norm-42%20standard-2b9348?style=flat-square)
![Stars](https://img.shields.io/github/stars/ifrankerem/minishell?style=flat-square)

</div>

> **As beautiful as a shell** — with [@ygtdmr](https://github.com/ygtdmr)

---

## 📋 Table of Contents

- [About](#about)
- [Features](#features)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [What You Can Try](#what-you-can-try)
- [Bonus](#bonus)
- [Under the Hood](#under-the-hood)
- [License](#license)

---

## 📖 About

**minishell** is a miniature **Bash** written in C. It executes commands,
chains them through pipes, redirects input and output, and manages the
environment — all in a lightweight, prompt-driven loop.

It's the 42 project that forces you to confront how a command interpreter works
under the hood: fork/exec, file descriptors, signal handling and a tokenizer
that has to agree with itself.

---

## ✨ Features

- Interactive command execution with a prompt
- Command chaining with pipes (`|`)
- Input/output redirection: `<`, `>`, `>>`, `<<` (heredoc)
- Signal handling: `Ctrl+C`, `Ctrl+D`, `Ctrl+\` behave like Bash
- Environment variables: `$HOME`, `$PATH`, `$?`
- Builtins: `echo`, `cd`, `pwd`, `env`, `export`, `unset`, `exit`
- Quoting: single and double quotes, backslash-style escapes
- A concrete parser → lexer → executioner pipeline

---

## 🧰 Getting Started

**Prerequisites**

- `gcc` or `clang`, `make`
- The **GNU Readline** library

**Build**

```sh
git clone https://github.com/ifrankerem/minishell.git
cd minishell
make
```

**Run**

```sh
./minishell
```

Exit with `exit` or `Ctrl+D`.

---

## 💻 Usage

```bash
$ ./minishell
minishell> echo Hello, world!
Hello, world!

minishell> ls -l | grep .c | wc -l
12

minishell> cd src
minishell> pwd
/home/user/minishell/src

minishell> export NAME=Minishell
minishell> echo $NAME
Minishell

minishell> echo "Goodbye!" > bye.txt
minishell> cat bye.txt
Goodbye!

minishell> exit
```

---

## 🪄 What You Can Try

- **Piping commands**
  ```bash
  cat file.txt | grep keyword | wc -l
  ```
- **Redirections**
  ```bash
  echo "hello" > file.txt
  cat < file.txt
  echo "again" >> file.txt
  ```
- **Environment variables**
  ```bash
  export NAME=Minishell
  echo $NAME
  unset NAME
  ```
- **Signal handling** — `Ctrl+C` clears the line for a new prompt, `Ctrl+D`
  exits, `Ctrl+\` `Ctrl+Z` pass through to Bash-like behaviour.

---

## 🌟 Bonus

- Logical operators `&&` and `||` with correct precedence
- Wildcard expansion (`*`) matching files in the working directory
- Heredocs that read into a pipeline, as `bash` does

---

## ⚙️ Under the Hood

The program is split into the usual shell pipeline:

| Stage | Files |
|---|---|
| Readline input and loop | `minishell.c` |
| Tokenizing | `lexer.c`, `lexer_utils.c` |
| Parsing into a command table | `parser.c`, `parser_utils.c` |
| Expansion | `expand.c`, `expand_utils.c` |
| Heredoc | `heredoc.c` |
| Execution | `executer.c`, `executer_utils.c` |
| Environment | `env_utils_1.c`, `env_utils_2.c` |

The design emphasises an environment table kept as a `NULL`-terminated array
of `KEY=value` strings, rebuilt whenever `export` or `unset` runs, and
correct signal masks around `fork`/`execve`/`wait` so the prompt stays
responsive.

---

## 📄 License

Built for the **42 Common Core** curriculum, shared for learning and portfolio
purposes. Respect the academic intent if you are a fellow student.

---

## 👤 Author

**İrfan Kerem Arslan** — [@ifrankerem](https://github.com/ifrankerem)
**Devrim** — [@ygtdmr](https://github.com/ygtdmr)

---

## 🙏 Acknowledgements

- [awesome-readme](https://github.com/matiassingers/awesome-readme) — structure inspiration for this README