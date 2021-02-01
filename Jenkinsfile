def gv
pipeline {
    agent any
    parameters {
        choice(name: 'VERSION', choices: ['1.0', '1.2', '1.3'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    
    stages {
        stage("init") {
            steps {
                script {
                    gv = load "script.groovy"
                    
                }
             }
        }
        
         stage("build") {
            steps {
                script {
                    gv = builApp() 
                }
             }
        }
        
        stage("test") {
            when {
                expression {
                      params.executeTests
                }
            }
            steps {
            script {
                    gv = testApp()   
                }
            }
        }
        
        stage("deploy") {
        
            steps {
            script {
                    gv = deployApp()   
                } 
            }
        }
   }
}
