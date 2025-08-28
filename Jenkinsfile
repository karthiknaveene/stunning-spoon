// Jenkinsfile_aborted.groovy

pipeline {
    agent any

    stages {
        stage('Build') {
            stages {
                stage('Compile') {
                    steps {
                        echo 'Compiling...'
                        sleep 1
                    }
                }
                stage('Package') {
                    steps {
                        echo 'Packaging...'
                        sleep 1
                    }
                }
            }
        }

        stage('Registering build artifact') {
            steps {
                echo 'Registering the metadata'
                echo 'Another echo to make the pipeline a bit more complex'
                registerBuildArtifactMetadata(
                    name: "test-artifact-1",
                    version: "1.0.1",
                    type: "docker",
                    url: "http://localhost:1111",
                    digest: "6f637064707039346163663237383938",
                    label: "qa"
                )
            }
        }

        stage('Test') {
            steps {
                echo 'Running Unit Tests...'
                sleep 10
                echo 'Running Integration Tests...'
                sleep 5
            }
        }

        
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sleep 5
                
                // Simulating Aborted Status
                script {
                    currentBuild.result = 'ABORTED'  // Marking the build as aborted
                    echo 'Build was aborted during deployment.'
                }
            }
        }
    }
}
