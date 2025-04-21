### Pipline script to task 2

```
pipeline {
 agent any
 stages {
  stage('Git') {
   steps {
    git branch: 'main', url: 'https://github.com/potapchuksa/netology-homework-08-automation-ci-cd-8-02-what-is-devops-ci-cd-materials.git'
   }
  }
  stage('Test') {
   steps {
    sh '/usr/local/go/bin/go test .'
   }
  }
  stage('Build') {
   steps {
    sh 'docker build . -t ubuntu-bionic:8082/hello-world:v$BUILD_NUMBER'
   }
  }
 }
}
```
