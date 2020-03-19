# Templates design

This tutorial will introduce you to view of what FreeMarker templates are and how you can use it to customize your KODO server.

[FreeMarker](http://www.freemarker.org) is a simple yet powerful template engine that KODO uses whenever administrator is allowed to customize part of KODO portal. In particular, it’s used to allow customization of e-mails that are send by KODO and myKODO download page.

In FreeMarker you define templates, which are text files that contain the desired output \(html in case of KODO\), except that they contain placeholders like `${username}`, and even some logic like conditionals. KODO will supply the actual values for these placeholders and the final output is generated based on this input.

Here is example of an simple FTL file:

```markup
<html>  
  <body>
    <p>Welcome ${user.username}. Thank you for using KODO!</p>
  </body>
</html>
```

In the template, use standard HTML+CSS features to define the appearance. CSS can be either included directly in the template file, or saved externally in a dedicated file.

With KODO you can also use FTL tag `<#if expression>...</#if>` it's similar to HTML tags, but they are instructions to FreeMarker and will not be printed to the output.

Example:

```markup
<html>
  <body>
    <p>Welcome ${user.username}. Thankk you for using KODO!<p>
    <#if includePassword>
      <p>Your new password is: ${user.password}</p>
    </#if>
  </body>
</html>
```

Some placeholders may return NULL string if some informations has not been set up. You can check it using FTL tag `<# variable??> ... </#if>`. If the variable contains NULL, the content between tags will not be displayed.

Example:

```markup
<html>
  <body>
    <p>Welcome ${user.username}. Thankk you for using KODO!<p>
    <#if links.downloadAndroid??>
      <p>Click <a href="${links.downloadAndroid}">HERE</a> to download KODO Android client</p>
    </#if>
  </body>
</html>
```

Some of the variables will store the collection of items that need to be displayed . In that case you will need to use list tag:

```text
<#list sequence as item>
    Part repeated for each item
</#list>
```

Example:

```text
<#list share.sources as source>  
<li>${source.path}</li>
</#list>
```

Example output:

```text
C:\Users\John\Desktop
C:\Users\John\Documets
C:\users\John\Pictures
```

KODO will look for **template.ftl** file in following paths:

* E-mail template for admin access of newly created organization `/opt/StorwareData/templates/adminAccess`
* E-mail template for user password change `/opt/StorwareData/templates/changePass`
* E-mail template for deployment e-mail `/opt/StorwareData/templates/deploy`
* E-mail template for daily report `/opt/StorwareData/templates/newsletter`

If the template file is not found default will be used.

