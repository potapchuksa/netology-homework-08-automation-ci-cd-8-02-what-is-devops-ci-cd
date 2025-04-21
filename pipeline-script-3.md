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
    sh 'CGO_ENABLED=0 GOOS=linux /usr/local/go/bin/go build -a -installsuffix nocgo -o ./app .'
    sh 'curl -u admin:admin http://158.160.43.170:8081/repository/my_repo/ --upload-file app -v'
   }
  }
 }
}
```
