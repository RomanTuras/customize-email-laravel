# How to customize email notifications in Laravel 8

### Generate class app/Notifications/NotifyUser.php

```
php artisan make:notification NotifyUser
```

### For use this NotifyUser class open a User model and add:

```php
public function sendPasswordResetNotification($token)
{
    $this->notify(new NotifyUser($token));
}
```

### In my case, I store translate messages in the:

_resources/lang/\_en/passwords.php_

### For publish the email templates:

```
php artisan vendor:publish --tag=laravel-notifications
```

_Result is: resources/views/vendor/notifications/email.blade.php_

### For publish all components:

```
php artisan vendor:publish --tag=laravel-mail
```

_The result will be in: /resources/views/vendor/mail_

### At last, for change a theme of email notification, go to:

_config/mail.php_

### and change the default theme

---

## For setup sending mail, open .env and

- change all founding `127.0.0.1` to `localhost`
- setup mail settings:

```
MAIL_MAILER=smtp
MAIL_HOST=smtp.nei**ica.com
MAIL_PORT=587
MAIL_USERNAME=info@nei**ica.com
MAIL_PASSWORD=***
MAIL_ENCRYPTION=null
MAIL_FROM_ADDRESS=info@nei**ica.com
MAIL_FROM_NAME="${APP_NAME}"
```
