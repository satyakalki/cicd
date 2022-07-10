node{

   def tomcatWeb = 'home/ec2-user/jenkins/apache-tomcat-10.0.22/webapps'
   def tomcatBin = 'home/ec2-user/jenkins/apache-tomcat-10.0.22/bin'
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://github.com/satyakalki/cicd.git'
   }
   stage('Compile-Package-create-war-file'){ 
     sh "mvn package"
      }
/*   stage ('Stop Tomcat Server') {
            sh ''' @Echo off
              kilall tomcat
			   if [ "$? -eq 0" ]; then 
				echo " stopped";
				else
					echo running
                  "${tomcatBin}\\shutdown.sh"
                  sleep 10
               fi
'''
   }*/
   stage('Deploy to Tomcat'){
     sh "cp target/JenkinsPipeline.war "${tomcatWeb}/""
   }
      stage ('Start Tomcat Server') {
         sleep 5 
         sh "${tomcatBin}\\startup.sh"
         sleep 10
   }
}
