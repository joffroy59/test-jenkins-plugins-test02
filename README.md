# test creation d'un plugin jenkins from scratch 

```
mvn -U org.jenkins-ci.tools:maven-hpi-plugin:create
	Enter the groupId of your plugin [org.jenkins-ci.plugins]: org.offroy.jenkins-ci.plugins
	Enter the artifactId of your plugin (normally without '-plugin' suffix): test02
```
**OK**

## import eclipse (import existing maven project)

### TEST execution :

#### en ligne de commande :

* mvn hpi:run -Djetty.port=8090
```
	http://localhost:8090/jenkins/ ok
	-> plugin installé mais pas de build dans la config d'un job
```

* mvn clean hpi:run -Djetty.port=8090
```
	http://localhost:8090/jenkins/ ok
	-> plugin installé et build present dans la config d'un job
	-> job ok : Hello, test! (class presente et descriptor de classe aussi...)
```

#### avec eclipse:

* mvn clean hpi:run -Djetty.port=8090
```
	http://localhost:8090/jenkins/ ok
	-> plugin installé et build present dans la config d'un job
	-> job ok : Hello, test! (class presente et descriptor de classe aussi...)
```

* clean dans eclipse

* mvn hpi:run -Djetty.port=8090
```
	http://localhost:8090/jenkins/ ok
	-> plugin installé et build present dans la config d'un job
	-> job ko : java.lang.AssertionError: class org.offroy.jenkinsci.plugins.test02.HelloWorldBuilder is missing its descriptor
```

### TEST debug :

#### en ligne de commande :

* mvnDebug clean hpi:run -Djetty.port=8090
```
	creation dans eclipse "Remote java application" (8000) 
	ajout d'un breakpoint dans la methode "perform"
	http://localhost:8090/jenkins/ ok
	-> plugin installé et build present dans la config d'un job
	-> job ok et break dans eclipse ok : Hello, test! (class presente et descriptor de classe aussi...)
```

* remplacement de code :
modification de la classe principale 
```
	http://localhost:8090/jenkins/ ok
	-> plugin installé et build present dans la config d'un job
	-> job ok et break dans eclipse ok : Hello2, test! (class presente et descriptor de classe aussi...)
```

	
**attention parfois la classe peut etre recompilé et eclipse ne la reconnait plus donc il ne donne pas les bonnes sources (en plus de forcer source lookup)**
