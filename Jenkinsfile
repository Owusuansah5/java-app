/*
pipeline {

    agent any
    environment {
      NEW_VERSION = '1.3.0'
    }

    stages {
	/*
	stage("Checkout") {

           steps {
                echo 'cloning application code from gitlab......'
           }
        }
	
	stage("build") {
	   
	   steps {
         script{

         }
		echo 'building the application......'
      echo "building version ${NEW_VERSION}"
	   }
	}
	stage("test") {

           steps {
                echo 'testing the application......'
           }
        }
	stage("deploy") {

           steps {
                echo 'deploying the application......'
           }
        }
    }

}
*/

pipeline {

    agent any
    tools {
        maven 'M2_HOME'
    }
    stages {
         stage("test") {

            steps {
                script {
                    echo "Testing the aplication..."
                    echo "executing pipeline for branch $BRANCH_NAME"
                    

                }
            }
        }
	
        stage("build jar") {
            when {
               expression {
                  BRANCH_NAME == "main"

               }
            }

            steps {
                script {
                    echo "bUilding the aplication..."
                    sh 'mvn clean package -DskipTests'

                }
            }
        }
        stage("build image") {

            steps {
                script {
                    echo "bUilding the docker image..."
                    withCredentials([usernamePassword(credentialsId: 'docker-login-cred', passwordVariable: 'PASS', usernameVariable: 'USER')]){
                        sh 'docker build -t owusuansah5/java-app:app.1.0 .'
                        sh 'echo $PASS | docker login -u $USER --password-stdin'
                        sh 'docker push owusuansah5/java-app:app.1.0'
                    }
                  }
            }
         }
         stage("Deploy") {

            steps {
                script {
                    echo "Deploying the aplication..."
                  echo "executing pipeline for branch $BRANCH_NAME"
                  

                }
            }
        }
      }
}
