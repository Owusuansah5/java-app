pipeline {


    agent any

    stages {
	
	stage("Checkout") {

           steps {
                echo 'cloning application code from gitlab......'
           }
        }
	stage("build") {
	   
	   steps {
		echo 'building the application......'
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

