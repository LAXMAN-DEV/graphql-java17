step 1:
$env:MAVEN_OPTS="--add-opens=java.base/java.util=ALL-UNNAMED --add-opens=java.base/java.lang=ALL-UNNAMED --add-opens=java.base/java.lang.reflect=ALL-UNNAMED --add-opens=java.base/java.util.regex=ALL-UNNAMED --add-opens=java.base/java.net=ALL-UNNAMED --add-opens=java.desktop/java.beans=ALL-UNNAMED --add-opens=java.xml/javax.xml.namespace=ALL-UNNAMED --add-exports=java.base/sun.net.www.protocol.jar=ALL-UNNAMED"; mvn clean package -DskipTests

step 2 clean mule repo cache:
Remove-Item -Recurse -Force "$env:USERPROFILE\.m2\repository\com\mulesoft\services\mule-module-graphql"

step 3:
mvn install:install-file -Dfile="target\mule-module-graphql-1.1.2-mule-plugin.jar" -DgroupId="com.mulesoft.services" -DartifactId="mule-module-graphql" -Dversion="1.1.2" -Dpackaging="jar" -Dclassifier="mule-plugin"


in app use:
mvn clean install -U
