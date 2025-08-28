pipeline {
    agent any

    stages {
        stage('Build') {
            stages {
                stage('Compile') {
                    steps {
                        echo 'Compiling...'
                        sleep 11
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
                    version: "1.0.2",
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
                sleep 1
                echo 'Running Integration Tests...'
                sleep 1
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sleep 1
            }
        }
    }
}
