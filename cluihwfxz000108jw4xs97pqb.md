---
title: "Basics Linux Commands, 
Part 2"
seoTitle: "Linux Commands"
seoDescription: "Commands helpful for Linux Operating system"
datePublished: Tue Apr 02 2024 14:49:34 GMT+0000 (Coordinated Universal Time)
cuid: cluihwfxz000108jw4xs97pqb
slug: basics-linux-commands-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1712069069878/5c7c529c-a904-442f-b837-76da43476a52.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1712069172951/a06604b6-cd64-4c36-a1c2-430f43a87c5f.png
tags: linux, devops, linux-for-beginners, deepeshmlgupta

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711828957391/9ff60711-8dc5-4cf3-abe3-cf39330f231f.png?auto=compress,format&format=webp align="left")

## Command to Create a Directory

```plaintext
mkdir <directory-name>
mkdir -v <directory-name>
```

mkdir command is used to create directory in Linux

\-v, --is used to print the action that is performed

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712065300892/69af5e0b-b85b-41ca-ae70-7cabd571a876.png align="center")

## Command to Create a Nested Directory (**A/B/C/D/E)**

```plaintext
mkdir -p A/B/C/D/E
```

mkdir command is used to create directory in Linux and -p makes parent directories as needed

\-p, --makes parent directories as needed

## **Command to remove Directory/Folder in Linux?**

To remove an empty directory,

```plaintext
rmdir <directory-name>
```

To remove empty directories,

```plaintext
rm -r <directory-name>
```

Here, -r means recursively, Or, it is used to delete the directory which consits of files inside it

## **Command to create a color.txt file and to view the content?**

To create a file "touch" command is used,

```plaintext
touch <filename>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689571050923/5c0220bc-17ca-450b-b8c4-102407796186.png?auto=compress,format&format=webp align="center")

To view the content of a file, the "cat" command is used,

```plaintext
cat <filename>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689571098498/3ff222ab-42ff-4d03-a147-57afcb2fa087.png?auto=compress,format&format=webp align="center")

## **Command to Add content in color1.txt**

First create a file with "touch" command,

Example: touch color1.txt

Open color1.txt file with nano editor,

***vim, nano editors are used to add content to a file.***

Example: nano color1.txt

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712066169500/3523d5d9-85b3-4409-a8f0-56556530386d.png align="center")

After adding content to the file press ctrl+x and y to save the file

## **Command to show only top three fruits from the file?**

**COPY**

**COPY**

```plaintext
head -3 <filename>
```

In the above command, the "head" command gives us first part of a file.

\-3, --shows the top 3 lines of a file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712066256905/e43b9848-c0ef-4435-a1ec-cdd4dd4bee21.png align="center")

## **Command to Show only bottom three fruits from the file.**

```plaintext
tail -3 <filename>
```

In the above command, the "tail" command gives us last part of a file.

\-3, --shows the bottom 3 lines of a file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712066359611/0134524c-e3b5-4e92-8c69-834c1571c27a.png align="center")

## **Command to find the difference between two files in Linux**

Let's create one file named color.txt

```plaintext
nano color.txt
```

add content to this file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712066722480/c5a6c022-2644-4ca5-97f1-b74160016868.png align="center")

Now, to find the difference between these files we simply run **diff** command

```plaintext
 diff color.txt color1.txt
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712066822682/77216e8a-3e92-4e0e-8193-5412cc3f5813.png align="center")