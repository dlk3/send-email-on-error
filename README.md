#  Send Notification e-Mail When A Service Fails

I created this to notify me when custom timer-triggered services I ctreated
failed due to errors.

Put send-email-on-error script in /usr/local/bin.  Make it executable.

Put send-email-on-error@.service in /etc/systemd/system.

Customize send-email-on-error.cfg and place in /etc/sysconfig.

Test the notification service by issuing the command:

    sudo systemctl start send-error-on-failure@dbus.service

To enable a service you create to use this notification service, include the 
following line in the [Unit] section of you services's systemd.service file:

    OnFailure=send-email-on-error@%n.service
