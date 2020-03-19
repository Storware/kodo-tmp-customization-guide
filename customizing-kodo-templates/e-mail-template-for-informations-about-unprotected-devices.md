# E-mail template for informations about unprotected devices

## **Template file:**

```bash
/opt/StorwareData/templates/unprotectedDevices/template.ftl
```

## **Available placeholders:**

### User:

* `${user.firstName}` - \(string\) KODO user first name, e.g. "Jon"
* `${user.lastName}` - \(string\) KODO user last name, e.g. "Doe"
* `${user.fullName}` - \(string\) KODO user first and last name, e.g. "Jon Doe"
* `${user.username}` - \(string\) KODO user login, e.g. "administrator"
* `${user.password}` - \(string\) KODO user password
* `${user.guid}` - \(string\) KODO user password

### Devices:

* `device` - \(list\) collection of unprotected devices
* `device.guid` - \(string\) GUID of the device
* `device.name` - \(string\) name of the device
* `device.lastLoginDate` - \(date\) date of last device login to KODO
* `device.lastBackupDate` - \(date\) date of last device backup to KODO
* `device.lastBackupDate` - \(date\) date of last device backup to KODO
* `device.os.desktop` - \(boolean\) true if desktop operating system 
* `device.os.mobile` - \(boolean\) true if mobile operating system

## **Default template:**

```markup
<html>
<head>
    <title>Kodo unprotected devices</title>
    <style>
        a {
            text-decoration: none;
        }
    </style>
</head>
<body style="text-align: center;margin:0;font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;color:#000;font-size:11pt;color:#808080;">

<div style="margin: 0 auto;width: 550px;text-align: left;">

    <div style="height: 140px;width: 550px;">
        <img alt="Kodo" src="cid:topcid"/>
    </div>

    <h3 style="margin-bottom:0px;color:#000;">Devices that are not protected</h3>
    <hr style="margin:0px;text-align:left;color:#d9261c;background-color:#d9261c;height:2px;border:0px;width:148px;"/>

    <p>
        Hi ${user.fullName},
    </p>

    <p>
        this email was sent to you by KODO administrator please do not respond to it.
    </p>
    <p>
        We would like to inform you that some of your devices are not protected.
    </p>


    <h3 style="margin-bottom:0px;color:#000;">Unprotected devices</h3>
    <hr style="margin:0px;text-align:left;color:#d9261c;background-color:#d9261c;height:2px;border:0px;width:155px;"/>

    <ul>
<#list devices as d>
    <li>${d.name} <#if d.os.desktop == true>(last seen: <#if d.lastLoginDate??>${d.lastLoginDate?string["yyyy-MM-dd HH:mm:ss"]}<#else>never</#if>)<#else>(last backup: <#if d.lastBackupDate??>${d.lastBackupDate?string["yyyy-MM-dd HH:mm:ss"]}<#else>never</#if>))</#if></li>
</#list>
    </ul>
<br/>
    <p>
        Thank you for using KODO
    </p>


</div>
</body>
</html>
```

