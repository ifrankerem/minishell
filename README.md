# 🐚 Minishell  
**As beautiful as a shell — developed by [@iarslan](https://github.com/iarslan) & [@ygtdmr](https://github.com/ygtdmr)**  

Minishell is a small UNIX-like shell written in C.  
It lets you execute commands, chain them together with pipes, redirect inputs and outputs, and manage environment variables — all within a lightweight, Bash-inspired environment.

---

## 🚀 Overview

Minishell acts as a **miniature Bash**, allowing you to:
- Type and execute commands interactively
- Combine multiple commands using pipes (`|`)
- Redirect input/output with `<`, `>`, `>>`, and `<<`
- Handle signals (`Ctrl+C`, `Ctrl+D`, `Ctrl+\`) just like in Bash
- Work with environment variables (`$HOME`, `$PATH`, `$?`)
- Use built-in commands such as `echo`, `cd`, `pwd`, `env`, `export`, `unset`, and `exit`

It’s a fully functional mini shell that helps you understand how command interpreters work behind the scenes.

---

## 🧰 Installation & Setup

### 1️⃣ Clone the repository
```bash
git clone https://github.com/iarslan/minishell.git
cd minishell
```

### 2️⃣ Build the project
Make sure you have `make` and the **GNU Readline** library installed.  
Then simply run:
```bash
make
```

### 3️⃣ Run Minishell
```bash
./minishell
```

### 4️⃣ Exit anytime
```bash
exit
```

---

## 💬 Example Usage

```bash
$ ./minishell
minishell> echo Hello, world!
Hello, world!

minishell> ls -l | grep .c | wc -l
12

minishell> cd src
minishell> pwd
/home/user/minishell/src

minishell> echo $HOME
/home/user

minishell> echo "Goodbye!" > bye.txt
minishell> cat bye.txt
Goodbye!

minishell> exit
```

---

## 🪄 What You Can Try

- 🔁 **Piping commands**
  ```bash
  cat file.txt | grep keyword | wc -l
  ```

- 📂 **Redirections**
  ```bash
  echo "hello" > file.txt
  cat < file.txt
  echo "again" >> file.txt
  ```

- 🧩 **Environment variables**
  ```bash
  export NAME=Minishell
  echo $NAME
  unset NAME
  ```

- 🧘 **Signal handling**
  - `Ctrl+C` → Clears line and shows a new prompt  
  - `Ctrl+D` → Exits shell  
  - `Ctrl+\` → Ignored (no effect)  

---

## 🌟 Bonus Features (Optional)

In the bonus version, you can also:
- Use logical operators `&&` and `||` with precedence
- Expand wildcards (`*`) to match files in the current directory

---

## 💡 Why This Project Matters

Minishell is a deep dive into:
- Process creation and management (`fork`, `execve`, `wait`)
- File descriptor and pipe handling
- Signal and terminal control
- Command parsing and environment management

It’s a practical learning experience for anyone exploring **system programming**, **UNIX internals**, or **42 curriculum fundamentals**.

---

## 📜 License

This project was built for educational purposes as part of the **42 School curriculum**.  
You’re welcome to explore, learn, and modify — but please respect its academic intent.

---

🧑‍💻 *Developed with care by [@iarslan](https://github.com/iarslan) & [@ygtdmr](https://github.com/ygtdmr)*
