def APPS = []
def REF = "abcd"
pipeline {
    agent any 
    stages {

        stage('Find app name to build') {
            steps {
                script {
                    if (REF != "") {
                        VALUESFILE = sh(returnStdout: true, script:'git --no-pager diff --name-only HEAD~1 | sort -u | awk \'BEGIN {FS=\"/\"} {print \$1}\' | uniq')
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

