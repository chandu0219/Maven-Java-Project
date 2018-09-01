#!groovy

node {
    currentBuild.result = "SUCCESS"

    try {

       stage('Checkout'){

          checkout scm
       }

       stage('Compiling'){

          bat 'mvn clean install'
       }
	   
      stage('Sonar') {
                    //add stage sonar
                    bat 'mvn sonar:sonar'
                }
	    
	stage('Checkstyle') {
                    bat 'mvn checkstyle:checkstyle'
                }

               stage('PMD') {
                    bat 'mvn pmd:check'
                }
      /* stage('mail'){

         mail body: 'project build successful',
                     from: 'chandu0219@gmail.com',
                     replyTo: 'chandu0219@gmail.com',
                     subject: 'project build successful',
                     to: 'chandu0219@gmail.com'
       }*/
	    
	    

    }
    catch (err) {

        currentBuild.result = "FAILURE"

           /* mail body: "project build error is here: ${env.BUILD_URL}" ,
                     from: 'chandu0219@gmail.com',
                     replyTo: 'chandu0219@gmail.com',
                     subject: 'project build successful',
                     to: 'chandu0219@gmail.com'
            */
        throw err
    }
}
