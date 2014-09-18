DbHttpSession
=============

Stores session data in database and transfer data when session is destroy.
Uses for check users online, user's last activity and last ip.


Add this to component section in config/main.php

``` PHP
'session' => array (
  'class' => 'application.components.DbHttpSession',
  'connectionID' => 'db',
  'sessionTableName' => 'session',
  'userTableName' => 'user'
),
```

Session table will be created automatically



##### Add columns to your user table:
```
ALTER TABLE user ADD user_id INT(11) NOT NULL, ADD last_ip VARCHAR(100) NOT NULL, ADD last_activity DATETIME NOT NULL
```

#### For Example:

Add this method to User model
```PHP
    public static function getOnlineUsers()
    {
        $sql = "SELECT session.user_id, user.name FROM session LEFT JOIN user ON user.id=session.user_id";
        $command = Yii::app()->db->createCommand($sql);
        
        return $command->queryAll();
    }
```
