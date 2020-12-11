pipeline {
    agent any
    options {
      timeout(time: 60, unit: 'SECONDS') 
    }
    stages {
                stage('Compile') {
                    steps {
                            bat 'mvnw.cmd clean compile -e'
                    }
                }
                stage('Unit') {
                    steps {
                            bat 'mvnw.cmd clean test -e'
                    }
                }
                stage('Jar') {
                    steps {
                            bat 'mvnw.cmd clean package -e'
                    }
                }
                //stage('SonarQube analysis') {
                //    steps {
                //            withSonarQubeEnv('sonar') {
                //                sh './mvnw org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
                //            }
                //    }
                //}
                //stage('Nexus Upload'){
                //    steps {
                //        nexusArtifactUploader(
                //        nexusVersion: 'nexus3',
                //        protocol: 'http',
                //        nexusUrl: 'localhost:8081',
                //        groupId: 'com.devopsusach2020',
                //        version: '0.0.1',
                //        repository: 'test-nexus',
                //        credentialsId: 'nexus',
                //        artifacts: [
                //            [artifactId: 'DevOpsUsach2020',
                //            classifier: '',
                //            file: 'G:/Jenkins/Tarea5/ejemplo-maven/build/DevOpsUsach2020-0.0.1.jar',
                //            type: 'jar']
                //        ]
                //        )
                //        }
                //}
                stage('Run') {
                    steps {
                            bat 'start mvnw.cmd spring-boot:run'
                    }
                }
                stage('Test') {
                    steps {
                            sleep(time: 10, unit: "SECONDS")
                            bat 'curl -X GET "http://localhost:8081/rest/mscovid/test?msg=testing"'
                    }
                }
        }
}