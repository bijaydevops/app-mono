def APPS = []
def REF = "abcd"
pipeline {
    // If you are running jenkins in a container use "agent { docker { image 'docker:18.09.0-git' }}"
    agent any 
    stages {

        stage('Find app name to build') {
            steps {
                script {
                    if (REF != "") {
                        VALUESFILE = sh(returnStdout: true, script:'git show --pretty="" --name-only')
                        echo "${VALUESFILE}"
                    
                        LIST = VALUESFILE.split('\n')
                        echo "${LIST}"
                        def MAP = [:]
                        for(String file in LIST) {
                            MAP.put(file.split('/')[0], "build");
                        }
                        APPS = MAP.keySet()
                        echo " Iam here"
                        echo "${APPS}"
                    }
                }
                echo "Changes in:${VALUESFILE}"
                echo "I am here" 
                echo "application to build:${APPS}"
            }
        }
        
    }

}

