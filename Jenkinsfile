pipeline {
    agent any
    tools {
        maven 'M3'
        jdk 'java'
    }
    stages {
        stage("Tools initialization") {
            steps {
<<<<<<< HEAD
                sh "sudo mvn --version"
                sh "sudo java -version"
=======
                sh "java -version"
                sh "sudo mvn --version"
>>>>>>> 2cfe060f49c2ef2147cf8ca47f5676675d870ed0
            }
        }
        stage("Checkout Code") {
            steps {
                checkout scm
            }
        }
        stage("Check Code Health") {
            when {
                not {
                    anyOf {
                        branch 'master';
                    }
                }
           }
           steps {
               sh "sudo mvn clean compile"
            }
        }
        stage("Run Test cases") {
            when {
                branch 'develop';
            }
           steps {
               sh "sudo mvn clean test"
            }
        }
        stage("Check Code coverage") {
            when {
                branch 'develop'
            }
            steps {
               jacoco(
                    execPattern: '**/target/**.exec',
                    classPattern: '**/target/classes',
                    sourcePattern: '**/src',
                    inclusionPattern: 'com/iamvickyav/**',
                    changeBuildStatus: true,
                    minimumInstructionCoverage: '30',
                    maximumInstructionCoverage: '80')
           }
        }
        stage("Build & Deploy Code") {
            when {
                branch 'master'
            }
            steps {
                sh "sudo mvn tomcat7:deploy"
            }
        }
    }
 }
