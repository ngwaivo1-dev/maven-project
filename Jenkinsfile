pipeline {
    agent any

    stages {
        stage('compile code') {
            steps {
              sh '/opt/maven/bin/mvn compile '
            }
        }
        stage('PMD code-review') {
            steps {
                sh '/opt/maven/bin/mvn -P metrics pmd:pmd  '
            }
            post {
                success{
                    recordIssues(tools: [pmdParser(pattern: '**/pmd.xml')])
                }
            }
        }
