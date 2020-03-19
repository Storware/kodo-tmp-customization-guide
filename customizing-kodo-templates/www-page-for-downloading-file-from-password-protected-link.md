# WWW page for downloading file from password protected link

**Template file:**

```bash
/opt/StorwareData/templates/myKodoDownload/template.ftl
```

## **Available placeholders:**

### KODO Server:

* `${postUrl}` - \(string\) url to use with password form
* `wrongPassword` - \(boolean\) true if wrong password has been submited

## **Default template:**

```markup
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <title>Kodo</title>
        <!-- Tell the browser to be responsive to screen width -->
        <meta content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no" name="viewport">
        <!-- Bootstrap 3.3.7 -->
        <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
        <!-- Font Awesome -->
        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.5.0/css/font-awesome.min.css">
        <style>
            html {
                font-family: Roboto, "Helvetica Neue", Arial, sans-serif;
                line-height: 1.4;
            }

            * {
                border-radius: 0 !important
            }
        </style>
    </head>
    <body class="hold-transition login-page">
        <div class="modal-dialog" style="margin-bottom:0;margin-top:15%;width:400px">
            <div class="modal-content">
                <div class="panel-body">
                    <center><i class="fa fa-lock" style="font-size: 8em;color:#ccc"></i></center>
<#if wrongPassword!false>
                    <div class="alert alert-warning">
                       <b>Wrong password</b> Please make sure you have the correct password
                    </div>
</#if>
                    <form role="form" action="${postUrl}" method="POST">
                        <fieldset>
                            <div class="form-group">
                                <input class="form-control ng-pristine ng-untouched ng-empty ng-invalid ng-invalid-required" placeholder="Password" name="password"
                                    ng-model="password" required="" type="password" value="">
                            </div>
                            <button style="border-radius: 20px !important;padding: 10px;    font-size: 11px;    padding: 9px 12px 8px 12px;    letter-spacing: 0.1em;"
                                role="button" type="submit" class="btn btn-primary col-md-offset-3 col-md-6">DOWNLOAD</button>
                        </fieldset>
                    </form>
                </div>
            </div>
        </div>
    </body>
</html>
```

