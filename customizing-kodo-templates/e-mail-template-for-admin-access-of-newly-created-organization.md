# E-mail template for admin access of newly created organization

## **Template file:**

```bash
/opt/StorwareData/templates/adminAccess/template.ftl
```

## **Available placeholders:**

### User:

* `${admin.firstName}` - \(string\) KODO administrator/operator first name, e.g. "Jon"
* `${admin.lastName}` - \(string\) KODO administrator/operator last name, e.g. "Doe"
* `${admin.fullName}` - \(string\) KODO administrator/operator first and last name, e.g. "Jon Doe"
* `${admin.username}` - \(string\) KODO administartor/operator login, e.g. "administrator"
* `${admin.password}` - \(string\) KODO administrator/operator password

### KODO Server:

* `${url}` - \(string\) KODO url address
* `${organization.name}` - \(string\) Name of KODO organization
* `${organization.guid}` - \(string\) GUID of KODO organization
* `${organization.expireDate}` - \(date\) Date of KODO trial expiration. This parameter will be NULL if organization is not created in trial mode.

## **Default template:**

```markup
<html>
<head>
    <title>KODO admin password</title>
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

    <h3 style="margin-bottom:0px;color:#000;">KODO admin access</h3>

    <hr style="margin:0px;text-align:left;color:#d9261c;background-color:#d9261c;height:2px;border:0px;width:148px;"/>

    <p>
        Hi ${admin.fullName},
    </p>
    <p>
        this email was sent to you by KODO administrator please do not respond to it.
    </p>
    <br/>
    <p>
        Please find below administrative account's credentials:
    </p>
    <p>
        Login: <b>${admin.username}</b>
    </p>
    <p>
        Password: <b>${admin.password}</b>
    </p>
    <br/>
    <p>
        To access KODO portal click <a href="${url}"><b>here</b></a>.
    </p>

<br/>
    <p>
        Thank you for using KODO
    </p>


</div>
</body>
</html>
```

