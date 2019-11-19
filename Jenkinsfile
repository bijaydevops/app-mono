def APPS = []
pipeline {
    // If you are running jenkins in a container use "agent { docker { image 'docker:18.09.0-git' }}"
    agent any {

    environment {
        GITHUB_HOOK_SECRET = "github-webhook-token-app-mono"
        //DOCKERHUB = credentials('dockerhub-credentials')
        DOCKERHUB_USR = ""
        DOCKERHUB_PSW = ""
    }

    stages {

        stage('Find app name to build') {
            steps {
                script {
                    if (REF != "") {
                        VALUESFILE = sh(returnStdout: true, script:'git show --name-only --pretty=""')
                        LIST = VALUESFILE.split('\n')
                        def MAP = [:]
                        for(String file in LIST) {
                            MAP.put(file.split('/')[0], "build");
                        }
                        APPS = MAP.keySet()
                        echo "${APPS}"
                    }
                }
                echo "Changes in:${VALUESFILE}"
                echo "application to build:${APPS}"
            }
        }
        
    }
    post {
        cleanup {
            deleteDir()
        }
    }
}
}
