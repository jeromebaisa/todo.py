# todo.py

A lightweight command-line task manager written in Python that helps you organize tasks by priority. Tasks are stored in YAML format and can be easily managed from the terminal.

## Features

* Add tasks to different priority levels:

  * **Now** (highest priority)
  * **Soon**
  * **Later**
  * **Maybe** (lowest priority)
* View your current task instantly
* List tasks with indexes
* Mark tasks as completed
* Store tasks in a YAML file
* Support custom storage locations using the `TODO_PATH` environment variable
* Optional simplified output mode

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/daviewales/todo.py.git
cd todo.py
```

### 2. Install dependencies

```bash
pip3 install -r requirements.txt
```

### 3. Add todo.py to your PATH

```bash
ln -s /path/to/todo.py ~/bin/todo
```

### 4. Verify installation

```bash
todo -h
```

---

## Quick Start

Add a task that needs immediate attention:

```bash
todo now "Finish homework"
```

Add a task for later:

```bash
todo later "Update resume"
```

View current tasks:

```bash
todo ls
```

Mark the current task as completed:

```bash
todo done
```

---

## Usage

### View Current Task

Running the command without arguments displays the highest-priority task.

```bash
todo
```

### Add Tasks

| Command      | Description                                          |
| ------------ | ---------------------------------------------------- |
| `todo now`   | Add task to the beginning of the active task list    |
| `todo soon`  | Add task to the end of the active task list          |
| `todo later` | Add task to the beginning of the secondary task list |
| `todo maybe` | Add task to the end of the secondary task list       |

Examples:

```bash
todo now "Submit project"
todo soon "Buy groceries"
todo later "Read a book"
todo maybe "Learn Rust"
```

#### Short Commands

| Full Command | Shortcut  |
| ------------ | --------- |
| `todo now`   | `todo n`  |
| `todo soon`  | `todo s`  |
| `todo later` | `todo l`  |
| `todo maybe` | `todo m`  |
| `todo list`  | `todo ls` |

---

### List Tasks

Display the top three tasks:

```bash
todo list
```

Display all tasks:

```bash
todo list --all
```

Display tasks in reverse order:

```bash
todo list --from-end
```

Display a specific number of tasks:

```bash
todo list 10
```

---

### Complete Tasks

Complete the current task:

```bash
todo done
```

Complete a specific task by index:

```bash
todo done 2
```

---

## Task Storage

Tasks are stored in a YAML file with the following structure:

```yaml
- Eat
- Sleep
---
- Clean
- Exercise
```

By default, tasks are saved in:

```text
~/.todo/todo.yml
```

The first list contains higher-priority tasks (`now` and `soon`), while the second list contains lower-priority tasks (`later` and `maybe`).

---

## Custom Storage Location

You can override the default storage location using the `TODO_PATH` environment variable.

Example:

```bash
TODO_PATH="~/Desktop" todo now "Sleep"
```

This creates the todo file inside the Desktop directory instead of the default location.

---

## Ugly Mode

By default, tasks are displayed inside a decorative border.

Enable plain text output using:

```bash
todo --ugly
```

or

```bash
todo -u
```

This mode is useful for small terminals or scripting.

---

## Running on Android (Termux)

Edit:

```bash
/data/data/com.termux/files/usr/etc/bash.bashrc
```

Add:

```bash
export TODO_PATH="~/storage/shared/todo"
alias todo="todo -u"
```

This stores tasks in shared storage and enables plain text output by default.

---

## Testing

Run the built-in doctests:

```bash
python3 -m doctest todo.py
```

Verbose output:

```bash
python3 -m doctest -v todo.py
```

Using nose:

```bash
nosetests --with-doctest todo.py
```
