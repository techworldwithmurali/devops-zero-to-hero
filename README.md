### Working with `rm`

1. **Removing Files:**
   - To remove a file `filename` forcefully (`-f`):
     ```
     rm -f filename
     ```
   - The `-f` flag ensures that the file is deleted without prompting for confirmation.

2. **Removing Directories:**
   - To remove a directory `directory` recursively and forcefully (`-r` and `-f`):
     ```
     rm -rf directory
     ```
   - Use with caution as it deletes the directory and its contents recursively without confirmation.

### Creating and Deleting Users

1. **Creating Users:**
   - To create a user `user_name`:
     ```
     useradd user_name
     ```
     or
     ```
     adduser user_name
     ```

2. **Checking User Information:**
   - To check if a user exists and view their details:
     ```
     id user_name
     ```
     or
     ```
     cat /etc/passwd
     ```

3. **Deleting Users:**
   - To delete a user `user_name` and remove their home directory and mail spool (`-r`):
     ```
     userdel -r user_name
     ```

### Creating and Deleting Groups

1. **Creating Groups:**
   - To create a group `group_name`:
     ```
     groupadd group_name
     ```

2. **Checking Group Information:**
   - To view groups and their details:
     ```
     cat /etc/group
     ```

3. **Deleting Groups:**
   - To delete a group `group_name`:
     ```
     groupdel group_name
     ```

4. **Adding Users to Groups:**
   - To add `user_name` to an existing `group_name`:
     ```
     usermod -a -G group_name user_name
     ```

### Working with `head`

- The `head` command displays the first few lines of a file.
- To display the first 10 lines of `filename`:
  ```
  head filename
  ```
- To display the first `num` lines (e.g., 5 lines) of `filename`:
  ```
  head -n 5 filename
  ```

### Working with `tail`

- The `tail` command displays the last few lines of a file.
- To display the last 10 lines of `filename`:
  ```
  tail filename
  ```
- To display the last `num` lines (e.g., 5 lines) of `filename`:
  ```
  tail -n 5 filename
  ```

### Working with `top`

- The `top` command provides a dynamic view of processes running on the system.
- To view system summary and processes:
  ```
  top
  ```

### Working with `free`

- The `free` command displays memory usage information.
- To display memory usage in a human-readable format:
  ```
  free -h
  ```
