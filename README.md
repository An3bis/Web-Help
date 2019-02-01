# MySQL - Create new user
GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost' IDENTIFIED BY 'password';
# MySQL - Disable password validation
uninstall plugin validate_password;
