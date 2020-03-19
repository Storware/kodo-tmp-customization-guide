# E-mail template for user password change

## **Template file:**

```bash
/opt/StorwareData/templates/changePass/template.ftl
```

## **Available placeholders:**

### User:

* `${user.firstName}` - \(string\) KODO user first name, e.g. "Jon"
* `${user.lastName}` - \(string\) KODO user last name, e.g. "Doe"
* `${user.fullName}` - \(string\) KODO user first and last name, e.g. "Jon Doe"
* `${user.username}` - \(string\) KODO user login, e.g. "administrator"
* `${user.password}` - \(string\) KODO user password
* `${user.guid}` - \(string\) KODO user password
* `includePassword` - \(boolean\) true if "Include user password" has been selected

## **Default template:**

```markup
<html>
<head>
    <title>KODO Password Changed</title>
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

    <h3 style="margin-bottom:0px;color:#000;">Password Changed</h3>

    <hr style="margin:0px;text-align:left;color:#d9261c;background-color:#d9261c;height:2px;border:0px;width:148px;"/>

    <p>
        Hi ${user.fullName},
    </p>

    <p>
        this email was sent to you by KODO administrator please do not respond to it.
    </p>

    <p>
        We would like to inform you that your password has been changed.
    </p>
<#if includePassword>
    <p>
        New password: <b>${user.password}</b>
    </p>
</#if>

<br/>
    <p>
        Thank you for using KODO
    </p>


</div>
</body>
</html>
```

