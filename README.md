DbHttpSession
=============

Stores session data in database and transfer data when session is destroy.
Uses for check users online, user's last activity, last ip and other user's information


Add this to component section in config/main.php
 
'session' => array (
  'class' => 'application.components.DbHttpSession',
  'connectionID' => 'db',
  'sessionTableName' => 'session',
  'userTableName' => 'user'
),


Session table will be created automatically



Add columns to your user table:
ALTER TABLE user ADD user_id INT(11) NOT NULL, ADD last_ip VARCHAR(100) NOT NULL, ADD last_activity DATETIME NOT NULL
