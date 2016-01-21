# test creation d'un plugin jenkins from scratch 

mvn -U org.jenkins-ci.tools:maven-hpi-plugin:create
	Enter the groupId of your plugin [org.jenkins-ci.plugins]: org.offroy.jenkins-ci.plugins
	Enter the artifactId of your plugin (normally without '-plugin' suffix): test02
OK

import eclipse (import existing maven project)

**test execution : ** 
en ligne de commande : 
`mvn hpi:run -Djetty.port=8090`
	http://localhost:8090/jenkins/ ok
	-> plugin installé mais pas de build dans la config d'un job

`mvn clean hpi:run -Djetty.port=8090`
	http://localhost:8090/jenkins/ ok
	-> plugin installé et build present dans la config d'un job
	-> job ok : Hello, test! (class presente et descriptor de classe aussi...)

avec eclipse:
`mvn clean hpi:run -Djetty.port=8090`
	http://localhost:8090/jenkins/ ok
	-> plugin installé et build present dans la config d'un job
	-> job ok : Hello, test! (class presente et descriptor de classe aussi...)
