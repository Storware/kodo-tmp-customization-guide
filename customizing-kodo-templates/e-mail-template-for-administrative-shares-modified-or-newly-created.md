# E-mail template for administrative shares \(modified or newly created\)

## **Template file:**

```bash
/opt/StorwareData/templates/share/template.ftl
```

## **Available placeholders:**

### User:

* `${user.firstName}` - \(string\) KODO user first name, e.g. "John"
* `${user.lastName}` - \(string\) KODO user last name, e.g. "Doe"
* `${user.fullName}` - \(string\) KODO user first and last name, e.g. "John Doe"
* `${user.username}` - \(string\) KODO user login, e.g. "administrator"
* `${user.password}` - \(string\) KODO user password
* `${user.guid}` - \(string\) KODO user password

### Shares:

* `${share.guid}` - \(string\) GUID of the share
* `${share.name}` - \(string\) name of the new or modified share
* `share.isNew` - \(boolean\) true if share is newly created
* `share.users` - \(list\) collection of users added to share
* `share.groups` - list\) collection of user groups added to share
* `share.sources` - \(list\) collection of paths added to share
* `share.sources.includeSubdirs` - \(boolean\) true if path also include access to subdirs

## **Default template:**

```markup
<html>
<head>
    <title>Kodo new share</title>
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

<#if share.isNew>
    <h3 style="margin-bottom:0px;color:#000;">New share</h3>
<#else>
    <h3 style="margin-bottom:0px;color:#000;">Share edited</h3>
</#if>
    <hr style="margin:0px;text-align:left;color:#d9261c;background-color:#d9261c;height:2px;border:0px;width:148px;"/>

    <p>
        Hi ${user.fullName},
    </p>

    <p>
        this email was sent to you by KODO administrator please do not respond to it.
    </p>
<#if share.isNew>
    <p>
        We would like to inform you that new share <b>${share.name}</b> for your files on ${share.sources[0].device.name} device has been created.
    </p>
<#else>
    <p>
        We would like to inform you that <b>${share.name}</b> share for your files on ${share.sources[0].device.name} device has been modified.
    </p>
</#if>

    <h3 style="margin-bottom:0px;color:#000;">Shared folders</h3>
    <hr style="margin:0px;text-align:left;color:#d9261c;background-color:#d9261c;height:2px;border:0px;width:155px;"/>

    <ul>
<#list share.sources as source>
    <li>${source.path}<#if source.includeSubdirs> (with subdirectories)</#if></li>
</#list>
    </ul>

    <h3 style="margin-bottom:0px;;color:#000;">Shared with</h3>
    <hr style="margin:0px;text-align:left;color:#d9261c;background-color:#d9261c;height:2px;border:0px;width:150px;"/>

    <ul>
<#list share.users as user>
    <li><a href="mailto:${user.email}">${user.fullName}</a></li>
</#list>
<#list share.groups as group>
    <li>${group.name} group</a></li>
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

