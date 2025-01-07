# File Permissions in Ansible
-  `mode` in ansible plays an major role in Ansible.
- `077` =  `----rwxrwx`
- `007` =  `-------rwx`
- `000`  = `---`

---


# Understanding Octal Notation in File Permissions
In Unix/Linux systems, file permissions can be represented using **octal notation**. This is a convenient way to specify the access rights granted to the file owner, group, and others.

## Octal Permission Breakdown

Each type of permission is represented by a specific number:

- **Read (`r`)**: 4
- **Write (`w`)**: 2
- **Execute (`x`)**: 1

Each digit in the octal notation is the sum of these values, representing different combinations of permissions:

| **Octal Value** | **Permissions** | **Symbolic Notation** |
|-------------|-------------        |-------------------    |
| 0           | No permissions      | ---                   |
| 1           | Execute only        | --x                   |  
| 2           | Write only          | -w-                   |
| 3           | Write and execute   | -wx                   |
| 4           | Read only           | r--                   |
| 5           | Read and execute    | r-x                   |
| 6           | Read and write      | rw-                   |
| 7           | Read, write, and execute | rwx              |


## Structure of Octal Notation

- The **first digit** (optional) represents special modes:
  - Set UID (`4`)
  - Set GID (`2`)
  - Sticky bit (`1`)
  
- The **second digit** represents the owner's permissions.
  
- The **third digit** represents the group's permissions.

- The **fourth digit** represents others' permissions.

## Examples of Octal Notation

### Example 1: `0644`

- **Owner**: Read and write (`6` = `r + w`)

- **Group**: Read (`4` = `r`)

- **Others**: Read (`4` = `r`)

**Equivalent symbolic notation**: `rw-r--r--`

### Example 2: `0755`

- **Owner**: Read, write, and execute (`7` = `r + w + x`)

- **Group**: Read and execute (`5` = `r + x`)

- **Others**: Read and execute (`5` = `r + x`)

**Equivalent symbolic notation**: `rwxr-xr-x`

### Example 3: `0777`
- **Owner**: Read, write, and execute (`7`)

- **Group**: Read, write, and execute (`7`)

- **Others**: Read, write, and execute (`7`)

**Equivalent symbolic notation**: `rwxrwxrwx`


### Example 4: `0700`

- **Owner**: Read, write, and execute (`7`)

- **Group**: No permissions (`0`)

- **Others**: No permissions (`0`)



**Equivalent symbolic notation**: `rwx------`



## Special Permissions in Octal

- **Set UID (`4`)**: Allows users to run the file with the file owner's privileges when set on executable files.

- **Set GID (`2`)**: Allows users to run the file with the group owner's privileges when set on executable files.

- **Sticky Bit (`1`)**: Typically used on directories to ensure that only the file's owner can delete or modify the file within the directory.


### Examples of Special Permissions



- **`2755`**: Set GID on, owner has full permissions, group and others have read and execute.

  - **Symbolic notation**: `rwxr-sr-x`

- **`1777`**: Sticky bit on, full permissions for everyone.

  - **Symbolic notation**: `rwxrwxrwt`

## Using Octal Notation in Ansible

In Ansible, octal notation is used to set file permissions through modules like `file`, `copy`, and `template`.


### Example 1: Setting Permissions with the `file` Module

```yaml
- name: Set permissions for a file
  ansible.builtin.file:
    path: /path/to/file
    mode: '0644'
    owner: root
    group: root
```
### Example 2: Copying a File with Specific Permissions
```yaml
- name: Copy a file with specific permissions
  ansible.builtin.copy:
    src: /local/path/to/file
    dest: /remote/path/to/file
    mode: '0755'
    owner: user
    group: group
 ```
### Example 3: Using Special Permissions
 ```yaml
- name: Set directory with Set GID and sticky bit
  ansible.builtin.file:
    path: /path/to/directory
    mode: '2775'
    state: directory
```
