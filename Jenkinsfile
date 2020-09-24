pipeline{
    agent {label 'java'}
    environment{
       PATH = "/usr/share/maven/bin:$PATH"
    }
    
    stages{
       stage('Git Checkout') {
            steps{
               
                gitCheckout(
                    
                    branch: "master",
                    url: "https://github.com/sravankumar77/simplewebapp.git"
                )
            }
        }
        
        stage("maven build"){
            steps{
                mavenBuild()
            }   
        } 
        
        
        stage("deploy"){
            steps{
                deployTomcat( 
                    war: "target/java-tomcat-maven-example.war"
                      )
                 
                //step([$class: 'DockerComposeBuilder', dockerComposeFile: 'docker-compose.yml', option: [$class: 'StartAllServices'], useCustomDockerComposeFile: true])
            }   
        }
        
    }   
}
