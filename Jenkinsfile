import java.text.SimpleDateFormat

pipeline {
       agent any
        stages{
            stage('Checkout GIT'){
                steps{
                    echo 'Pulling...';
                    git branch: 'main',
                    url : 'https://github.com/khalsibadis/devopsBack.git';
                             }
                             }
            stage('Date') {
                steps {
                     script{
                     def date = new Date()
                     sdf = new SimpleDateFormat("MM/dd/yyyy")
                     println(sdf.format(date))
                             }
                             }
                             }
            stage('MVN CLEAN')
            {
                steps{
                sh  'mvn clean'
                }
            }
            stage('MVN COMPILE')
            {
                steps{
                sh  'mvn compile'
                }
            }
             stage('MVN SONARQUBE ')
                        {
                            steps{
                            sh  'mvn sonar:sonar -Dsonar.login=admin -Dsonar.password=sonar'
                            }
                        }
                        stage("nexus deploy"){
                                       steps{
                                               sh 'mvn  deploy'
                                       }
                                  }
                            

	}
}