# Navigation

## Overview
- Learning how to navigate the file system.

## Main Points
### 1. File System
- `Unix` and `Windows` store all files and directories in a _hierarchical directory structure_.
- `Unix-like systems` presents all files and directories under a single file system.
- `Linux` has a single root `/` for the whole file system.
- `Windows` assigns a drive letter (C:, D:, etc) to each partition or storage device. Each drive has its own file system.
- `mounting` is the process of making a storage device's file system accessible at a specific directory within the existing file system tree.

### 2. Filenames
- `Linux`:
  - Filenames are case sensitive e.g. `filename` and `Filename` are not the same.
  - It's recommended to use `.`, `_`, `-`; other symbols work but can cause issues scripts or shells.
  - It does not rely on _file extension_ to determine file type. It uses file metadata instead.

### 3. Pathnames
- `absolute` starts from the root dir `/` and specifies the full path to a file or directory.
- `relative` specifies the path to a file or directory starting from the current working directory.

## Examples
  ```bash
  # display the working dir
  pwd

  # list the contents of the current dir
  ls

  # change the working dir to '/etc'
  cd /etc

  # change the working dir to the user's home dir
  cd

  # change the working dir to the previous working dir
  cd -

  # change the working dir to a specific user's home dir
  cd ~user_name
  ```

## Questions
- What is the file system in low level? and how it's structured? and how does it work?