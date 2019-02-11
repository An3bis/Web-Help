# MySQL - Create new user
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';

GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost' IDENTIFIED BY 'password';

flush privileges;
# MySQL - Disable password validation

uninstall plugin validate_password;
