@Library("shared-lib") _
pipeline {
    agent {label "demo"}
    stages{
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("code") {
            steps {
            script{
            clone("https://github.com/dhruvenp/django-notes-app.git","main")    
            }
        }
        }
        stage("build"){
            steps {
            script{
            docker_build("django-prod","dev","dhruvenp")    
            }
            }
       }
       stage("push"){
           steps{
               script{
                 docker_push("django-prod","dev","dhruvenp")  
                   
               }
           }
        }
       
       
       stage("test"){
           steps{
               echo "this is the test stage"
           }
       }
       
       stage("deploy")
       {
         steps{
           script{
              deploy("dhruvenp/django-prod","dev","7001","8000")
           }       
         }
       }
        
    }
}
