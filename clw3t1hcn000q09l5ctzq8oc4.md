---
title: "Shell Scripting for DevOps Engineers"
datePublished: Sun May 12 2024 17:24:17 GMT+0000 (Coordinated Universal Time)
cuid: clw3t1hcn000q09l5ctzq8oc4
slug: shell-scripting-for-devops-engineers
tags: bash, cloud-computing, devops, shell-script, deepeshmlgupta

---

## **What is Shell Scripting for DevOps?**

Shell scripting is a list of commands in a computer program that is run by UNIX shell which is a command line interpreter. Shell scripting helps to automate day-to-day manual tasks and reduce human intervention. This also helps to reduce human errors and time.

> ***Note: Extension of shell script must be ".sh"***

Let's look at this basic example of shell script,

Steps:

1. Create a new file and open the file,
    

```plaintext
vi echo.sh
```

1. Enter the following code,
    

```plaintext
#!/bin/bash
#Author: Madhup Pandey
#Date: 18/07/2023
#Purpose: This script will print some statement on terminal

echo "I will be a great DevOps Engineer"
```

1. Save the file with the following,
    

> ***Esc + :wq***

Here, the "echo" command will print "I will be a great DevOps Engineer" on the terminal.

1. Give execute permission to the file,
    

```plaintext
chmod 777 echo.sh
```

1. execute a shell script with the following command,
    

```plaintext
./echo.sh
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689657520287/5efb98a9-aaef-4512-8150-25baf1ce4b8a.png?auto=compress,format&format=webp align="left")

---

## What is `#!/bin/bash?` can we write `#!/bin/sh` as well?

#!/bin/bash tells the interpreter which shell should be used to execute the shell script.

#!/bin/bash is called a shebang line.

Yes, We can use either,

> ***#!/bin/bash***
> 
> ***#!/bin/sh***

Both the shebang lines mentioned above are correct.

> ***Note: Use only one of them ( Shebang lines ).***

---

## Write a Shell Script which prints `I will become a successful DevOps Engineer`

```plaintext
#!/bin/sh
#Author: Madhup Pandey
#Date: 18/07/2023
#Purpose: This script will print some statement on terminal

#Printing statement
echo "I will become a successful DevOps Engineer"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689658270291/a9bb2738-7490-4732-8b4d-b9ac7daf95bd.png?auto=compress,format&format=webp align="left")

---

## Write a Shell Script to take user input, input from arguments and print the variables.

```plaintext
#!/bin/sh
#Author: Madhup Pandey
#Date: 18/07/2023
#Purpose: This shell script will accept 2 Arguments from user and displays it

#Defining Variables
Arg1=$1
Arg2=$2

#Printing Variables
echo "First argument: $Arg1"
echo "Second argument: $Arg2"
```

Here,

Arg1, --Variable1

Arg2, --Variable2

Execute it with,

```plaintext
./input.sh madhup pandey
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689660536943/08d27052-3931-414e-a717-991858b39ec5.png?auto=compress,format&format=webp align="left")

---

## Write an Example of If else in Shell Scripting by comparing 2 numbers.

```plaintext
#!/bin/sh
#Author: Madhup Pandey
#Date: 18/07/2023
#Purpose: This shell script will compare 2 numbers using if else

#Defining Variables
Num1=8
Num2=10

#Comaring Variables
if [ $Num1 -lt $Num2 ]
then
        echo "$Num1 is greater than $Num2"
elif [ $Num1 -eq $Num2 ]
then
        echo "$Num1 is equal to $Num2"
else
        echo "$Num1 is lesser than $Num2"
fi
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689659314071/28d09e4d-6739-408a-87ec-811d88974ae3.png?auto=compress,format&format=webp align="left")

## **Write a bash script** [**create**](http://createdirectories.sh/) [**directories.sh**](http://directories.sh) [**that when the script**](http://createdirectories.sh/) **is executed with three given arguments (one is directory name and second is start number of directories and third is the end number of directories ) it creates specified number of directories with a dynamic directory name.**

```plaintext
#!/bin/bash
#############################################################
#Author: Madhup Pandey
#Date: 19/07/2023
#Purpose: This script will create 90 directories at once
#############################################################

#Intializing variables
Name_of_dir=$1
start_no=$2
end_no=$3

#Command to create directories
eval mkdir $Name_of_dir{$start_no..$end_no}
```

Here, "eval" command takes arguments as in[put to the command an](http://createdirectories.sh/)d stores it as one single command.

Execution,

```plaintext
./directories.sh day 1 90
```

[Here,](http://createdirectories.sh/)

[day, --First argument](http://createdirectories.sh/)

1, --Second [argument](http://createdirectories.sh/)

[2, --Third Argumen](http://createdirectories.sh/)t

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689742935846/0d8d80a5-1669-4e0a-9ab7-efef84fcbd70.png?auto=compress,format&format=webp align="left")

---

## [create a Script to](http://createdirectories.sh/) [backup all your work](http://createdirectories.sh/) do[ne till now](http://createdirectories.sh/)

```plaintext
##########################################################################
#Author: Madhup Pandey
#Date: 19/07/2023
#Purpose: This script will take backup
##########################################################################

#Creating Variables 
src=/home/ubuntu/day5
dest=/home/ubuntu/backups
time=$(date +"%Y-%m-%d-%H-%M-%S")
backupfile=$dest/$time.tgz

#Taking Backup
echo "Taking backup on $time"
tar zcvf $backupfile --absolute-names $src

if [ ${?} -eq 0 ]
then
        echo "Backup Complete"
else
        exit 1
fi
```

Above, script will take backups.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689753940807/cfc68758-9ef9-4b39-91ae-6f30a4624467.png?auto=compress,format&format=webp align="left")

---

## Read A[bout Cron and Crontab](http://createdirectories.sh/), to automate t[he backup Script](http://createdirectories.sh/)

```plaintext
crontab -e
```

Enter the below c[ode in the last line of crontab,](http://createdirectories.sh/)

```plaintext
* * * * * sh /home/ubuntu/day5/backup.sh
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689754605450/8fe97926-3e92-484d-b5d8-8fca52c01f26.png?auto=compress,format&format=webp align="left")

[first \*, --re](http://createdirectories.sh/)presents minutes

second \*, -[\-represents hours](http://createdirectories.sh/)

[th](http://createdirectories.sh/)ird \*, --r[epresents day of mont](http://createdirectories.sh/)h

fourth [\*, --represents mont](http://createdirectories.sh/)h

fith \*, --da[y of week](http://createdirectories.sh/)

---

## [Read abou](http://createdirectories.sh/)t User Ma[nagement](http://createdirectories.sh/)

[User manage](http://createdirectories.sh/)men[t is a very important](http://createdirectories.sh/) part o[f DevOps engineer's j](http://createdirectories.sh/)ourney.

User management includes some basic tasks, [like](http://createdirectories.sh/)

* [Creating Use](http://createdirectories.sh/)rs
    
* Deleting Users
    
* Passwo[rd reset](http://createdirectories.sh/)
    
* [Adding user in a group](http://createdirectories.sh/)
    

---

## [Create 2 users and just display thei](http://createdirectories.sh/)r User[names](http://createdirectories.sh/)

```plaintext
##########################################################################
#Author: Madhup Pandey
#Date: 19/07/2023
#Purpose: This script will take two argument as username and create user
##########################################################################

#Creating variables
user1=$1
user2=$2

#Creating Users
echo "Adding Users $user1 and $user2"
useradd -p test -m $user1
useradd -p test -m $user2

if [ ${?} -eq 0 ]
then
        echo "Users added successfully"
else
        exit 1
fi
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689755682604/7070254d-f58e-4e99-b6b9-355d1b660a76.png?auto=compress,format&format=webp align="left")