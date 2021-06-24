# How to customize email notifications in Laravel 8 

Generate class app/Notifications/NotifyUser.php
php artisan make:notification NotifyUser

For use this NotifyUser class open a User model and add:
public function sendPasswordResetNotification($token)
{
    $this->notify(new NotifyUser($token));
}

For publish the email templates:
php artisan vendor:publish --tag=laravel-notifications
Result: resources/views/vendor/notifications/email.blade.php

For publish all components:
php artisan vendor:publish --tag=laravel-mail
The result will be in: /resources/views/vendor/mail

At last, for change a theme of email notification, go to:
config/mail.php
and change the dafault theme
