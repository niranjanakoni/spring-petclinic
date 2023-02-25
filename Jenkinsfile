pipeline {
        agent { label 'JDK17' }
        triggers {
                cron('0 * * * *')
        }
        stages {
                stage ('SourceCode') {
                        steps {
                                git url: 'https://github.com/niranjanakoni/spring-petclinic.git', branch: 'main'
                        }
                }
                stage ('Build the code') {
                        steps {
                                sh script: '/opt/maven/bin/mvn clean package'
                        }
                }
                stage ('Reporting & Archiving') {
                        steps {
                                 junit testResults: 'target/surefire-reports/*.xml'
                        }
                }
        }
        post {
                success {
                        echo "Success"
                }
                unsuccessful {
                        echo "Failure"
                }
        }
}

