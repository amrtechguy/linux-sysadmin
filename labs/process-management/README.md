# Process Management

## Tasks

### 1. Inspect Running Processes
- [x] List all processes owned by your current user.

```bash
ps -fu $USER
```

- [x] Show only their PID and command name.

```bash
ps -u $USER -o pid,comm
```

- [x] Find the parent process of your current shell and display its details.

```bash
ps -p $(ps -p $(echo $$) -o ppid=) -f
```

### 2. Trace Process Hierarchy

- [x] Starting from your current shell, follow its parent processes until you reach the init/systemd process.

```bash
pstree -ps $(echo $$)
```

- [x] At each step, display the command name, its arguments, and its PID.

```bash
pstree -aps $(echo $$)
```

### 3. Analyze Resource Usage

- [x] List all processes owned by your user.

```bash
ps -fu $USER
```

- [x] Show CPU and memory usage for each.

```bash
ps -u $USER -o pid,ppid,uid,cmd,%cpu,%mem
```

- [x] Sort to find the top CPU consumers.

```bash
ps -u $USER -o pid,ppid,uid,cmd,%cpu,%mem --sort=-%cpu
```

- [x] Sort to find the top memory consumers.

```bash
ps -u $USER -o pid,ppid,uid,cmd,%cpu,%mem --sort=-%mem
```

### 4. Manage Jobs in the Shell

- [x] Start a long-running background job.

```bash
xlogo &
```

- [x] List jobs running in the background.

```bash
jobs
```

- [x] Bring a job to the foreground.

```bash
fg %<jobspec>
```

- [x] Send a job back to the background.

```bash
CTRL+Z
```

### 5. Signals & Process Control

- [x] Start a test process and stop it with a signal.

```bash
xlogo &
kill -TSTP <pid>
jobs
```

- [x] Resume the stopped process.

```bash
jobs
kill -CONT %<jobspec>
jobs
```

- [x] Gracefully terminate a process.

```bash
jobs
kill -TERM %<jobspec>
jobs
```

- [x] Force-kill a process.

```bash
jobs
kill -KILL %<jobspec>
jobs
```

## Notes
- `pstree`: its output attributes of processes are limited.
- `ps`: maybe `%cpu` reads `+%100`, because `%cpu` in `ps` shows the sum across all cores or multiple used threads.
