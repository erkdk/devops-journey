#### Problem:
- Learn how to tar and untar files. 

#### Solution:

```
tar [options] [archive-name] [files...]
```
#### options:

| Flag | Meaning | Used For                  |
| ---- | ------- | ------------------------- |
| `-c` | Create  | Make a new archive        |
| `-x` | Extract | Unpack an archive         |
| `-z` | Gzip    | Compress/decompress `.gz` |
| `-v` | Verbose | Show progress             |
| `-f` | File    | Specify archive name      |

- List
```
erkdk@my-lab:~$ ls
devops-journey  file1.txt  hello.c  output.txt
```

- Create a compressed archive named myfiles.tgz:
```
erkdk@my-lab:~$ tar -czvf myfiles.tgz hello.c file1.txt output.txt
hello.c
file1.txt
output.txt
```
- explanation
```
1. Action
-c → create a new archive

2. Compression
-z → use gzip → output becomes .tgz (compressed)

3. Output visibility
-v → prints each file added:
hello.c
file1.txt
output.txt

4. File specification
-f myfiles.tgz → archive name
```

- See .tgz file:
```
erkdk@my-lab:~$ ls
devops-journey  file1.txt  hello.c  myfiles.tgz  output.txt
erkdk@my-lab:~$ 
```

- Verify contents without extracting
```
erkdk@my-lab:~$ tar -tzvf myfiles.tgz 				( -t -> list contents)
-rw-rw-r-- erkdk/erkdk      74 2026-04-02 07:50 hello.c
-rw-rw-r-- erkdk/erkdk      23 2026-04-02 05:51 file1.txt
-rw-rw-r-- erkdk/erkdk      36 2026-04-02 06:37 output.txt
erkdk@my-lab:~$ 
```

```
erkdk@my-lab:~$ rm file1.txt hello.c output.txt
erkdk@my-lab:~$ ls
devops-journey  myfiles.tgz
erkdk@my-lab:~$
```

- Extract
```
erkdk@my-lab:~$ tar -zxvf myfiles.tgz				( -x -> extract)
hello.c
file1.txt
output.txt
erkdk@my-lab:~$ ls
devops-journey  file1.txt  hello.c  myfiles.tgz  output.txt
erkdk@my-lab:~$
```
---
- Combined command:
```
tar -czvf files.tar.gz a.txt b.txt
```
This is equivalent to:
```tar -cvf files.tar a.txt b.txt
gzip files.tar
```
---

- tar → groups files
- gzip → compresses them

#### tar vs gzip :

| Feature         | `tar`                       | `gzip`                          |
| --------------- | --------------------------- | ------------------------------- |
| Purpose         | **Archiving (packaging)**   | **Compression**                 |
| Combines files? | Yes (many → one `.tar`)     | No (one file at a time)         |
| Compresses?     | No (by itself)              | Yes                             |
| Output          | `.tar`                      | `.gz`                           |
| Keeps structure | Yes (directories, metadata) | Not relevant (single file only) |

---
