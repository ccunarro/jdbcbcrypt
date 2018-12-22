# jdbcbcrypt
Adapting JDBCRealm to support bcrypt(https://en.wikipedia.org/wiki/Bcrypt) passwords for basic authentication with Tomcat 8.

Documentation
https://tomcat.apache.org/tomcat-7.0-doc/realm-howto.html#JDBCRealm

Problem:

- Needed to configure basic authentication with Tomcat and a database. 
- The passwords of the users table were encrypted using bcrypt so using the default JDBCRealm implementation was not enough as it is not supported.

Solution:
- Small modification to the JDBCRealm tomcat implementation: https://github.com/apache/tomcat80/blob/trunk/java/org/apache/catalina/realm/JDBCRealm.java
- Generate jar with maven and copy to $CATALINA_HOME/lib folder (you will also need to copy the bcrypt jar to $CATALINA_HOME/lib). 
- Reference the customized realm from your server.xml realm configuration (check server.xml example on this project).
- Restart tomcat.
