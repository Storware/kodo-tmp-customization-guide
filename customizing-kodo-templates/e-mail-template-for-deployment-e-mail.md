# E-mail template for deployment e-mail

## **Template file:**

```bash
/opt/StorwareData/templates/deploy/template.ftl
```

## **Available placeholders:**

### User:

* `${user.firstName}` - \(string\) KODO user first name, e.g. "Jon"
* `${user.lastName}` - \(string\) KODO user last name, e.g. "Doe"
* `${user.fullName}` - \(string\) KODO user first and last name, e.g. "Jon Doe"
* `${user.username}` - \(string\) KODO user login, e.g. "administrator"
* `${user.password}` - \(string\) KODO user password
* `${user.guid}` - \(string\) KODO user GUID
* `includePassword` - \(boolean\) true if "Include user password" has been selected

### Client download links:

* `${links.downloadWindowsX86}` - \(string\) link to KODO client for Windows x86, empty if client package not uploaded to server
* `${links.downloadWindowsX64}` - \(string\) link to KODO client for Windows x64, empty if client package not uploaded to server
* `${links.downloadOsx}` - \(string\) link to KODO client for Mac OS, empty if client package not uploaded to server
* `${links.downloadAndroid}` - \(string\) link to KODO client for Android, empty if client package not uploaded to server
* `${links.mobileMagic}` - \(string\) magick link for mobile devices
* `${links.desktopMagic}` - \(string\) magick link for desktop devices
* `desktopDeployment` - \(boolean\) true if desktop deployment
* `mobileDeployemnt` - \(boolean\) true if mobile deployment

## **Default template:**

```markup
<html>
<head>
    <title>Kodo installation</title>
</head>
<body style="text-align: center;margin:0;font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;color:#000;font-size:11pt;color:#808080;">

<div style="margin: 0 auto;width: 550px;text-align: left;">

    <div style="height: 140px;width: 550px;">
        <img alt="Kodo" src="cid:topcid"/>
    </div>

    <h3 style="margin-bottom:0px;color:#000;">Installation Guide</h3>
    <hr style="margin:0px;text-align:left;color:#d9261c;background-color:#d9261c;height:2px;border:0px;width:148px;"/>

    <p>
        Hi ${user.fullName},
    </p>

    <p>
        this email was sent to you by KODO administrator please do not respond to it.
    </p>

    <p>
        In next couple steps we will help you install KODO application on your laptop and phone.
    </p>

<#if desktopDeployment!false>
    <h3 style="margin-bottom:0px;color:#000;">Laptop Installation</h3>
    <hr style="margin:0px;text-align:left;color:#d9261c;background-color:#d9261c;height:2px;border:0px;width:155px;"/>
    <p>
        Please install the correct package depending on your operating system.
    </p>

    <table>
    <tr>
<#if links.downloadWindowsX86??>
        <td width="100" align="center" valign="middle">
            <a style="border:none" href="${links.downloadWindowsX86}">
                <img alt="Windows" src="cid:wincid"/><br/>
                (32-bit)
            </a>
        </td>
</#if>
<#if links.downloadWindowsX64??>
        <td width="100" align="center" valign="middle">
            <a style="border:none" href="${links.downloadWindowsX64}">
                <img alt="Windows" src="cid:wincid"/><br/>
                (64-bit)
            </a>
        </td>
</#if>
<#if links.downloadOsx??>
        <td width="100" align="center" valign="middle">
            <a style="border:none" href="${links.downloadOsx}">
                <img alt="OS X" src="cid:ioscid"/><br/>
            </a>
        </td>
</#if>
    </tr>
    </table>

    <p>
        When application is installed you can configure it manually or using:<br/>
        <p><a style="color:#FF8C00;font-weight:500;" href="${links.desktopMagic}">Magic Link</a></p><br/>
    </p>
</#if>

<#if mobileDeployment!false>
    <h3 style="margin-bottom:0px;;color:#000;">Phone Installation</h3>
    <hr style="margin:0px;text-align:left;color:#d9261c;background-color:#d9261c;height:2px;border:0px;width:150px;"/>

    <p>
        Please install the correct package depending on your phone.
    </p>

    <table>
    <tr>
    <!--
        <td width="100" align="center" valign="middle">
            <a style="border:none" href="https://www.microsoft.com/pl-pl/store/apps/storware-mobile/9nblggh0dmhn">
                <img alt="Windows" src="cid:wincid"/>
            </a>
        </td>
    //-->
        <td width="100" align="center" valign="middle">
            <a style="border:none" href="https://play.google.com/store/apps/details?id=eu.storware.kodo">
                <img alt="Android" src="cid:androidcid"/><br/>
<#if links.downloadAndroid??>
                Google Play
</#if>
            </a>
        </td>
<#if links.downloadAndroid??>
        <td width="100" align="center" valign="middle">
            <a style="border:none" href="${links.downloadAndroid}">
                <img alt="Android" src="cid:androidcid"/><br/>
                APK file
            </a>
        </td>
</#if>
        <td width="100" align="center" valign="middle">
            <a style="border:none" href="https://itunes.apple.com/us/app/storware-kodo/id1075813002">
                <img alt="iOS" src="cid:ioscid"/>
            </a>
        </td>
    </tr>
    </table>

    <p>
        When application is installed you can configure it manually or using:<br/>
        <p><a style="color:#FF8C00;font-weight:500;" href="${links.mobileMagic}">Magic Link</a></p><br/>
        <b><i style="font-size:10pt;">Please remeber that the magic link will only work if you use it on your phone</i></b>
    </p>
</#if>

<br/>
    <p style="font-size:10pt;">
        For manual configuration:<br/>
        Server address: <b>${serverAddress}</b><br/>
        Username: <b>${user.username}</b><br/>
    </p>

    <p>
        Thank you for using KODO
    </p>


</div>
</body>
</html>
```

