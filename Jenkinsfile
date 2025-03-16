pipeline { agent any

tools{

    maven 'maven'
}
stages{ stage('Git checkout'){

steps{

    git branch: 'master', url: 'https://github.com/Srikavya-1/onlinebookstore.git'

}
}

stage('clean and install'){

steps{

  sh 'mvn clean install'

}
}

stage('Package'){

steps{

  sh 'mvn package'

}
}

stage('Archive the Artifacts'){

steps{

  sh 'mvn clean install'
}
post{
    success{

        archiveArtifacts artifacts: '**target/*.war'
    }
}

}
stage('Test Cases'){

steps{

  sh 'mvn test'

}
}

stage('Deploy to tomcat server'){

steps{

  deploy adapters: [tomcat9(credentialsId: 'tomcat9credentials', path: '', url: 'http://localhost:8080/')], contextPath: 'IfocusSolutions', war: '**/*.war'

}
}

} }