Library('my-shared-library@main') 
pipeline {
    agent any

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-17-openjdk-amd64'
        MAVEN_HOME = '/usr/share/maven'
        PATH = "${JAVA_HOME}/bin:${MAVEN_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout Code') {
            steps {
                script {
                    pipeline.check_out()
                }
            }
        }

        stage('Set up Java 17') {
            steps {
                script {
                    pipeline.setup_java()
                }
            }
        }

        stage('Set up Maven') {
            steps {
                script {
                    pipeline.setup_maven()
                }
            }
        }

        stage('Build with Maven') {
            steps {
                script {
                    pipeline.build_project()
                }
            }
        }

        stage('Upload Artifact') {
            steps {
                script {
                    pipeline.upload_artifact(String artifactPath)
                }
            }
        }

        stage('Run Application') {
            steps {
                script {
                    pipeline.run_application()
                }
            }
        }

        stage('Validate App is Running') {
            steps {
                echo 'Validating that the app is running...'
                script {
                    pipeline.validate_app()
                }
            }
        }

        stage('Wait for 2 minutes') {
            steps {
                echo 'Waiting for 2 minutes...'
                sleep(time: 2, unit: 'MINUTES')  // Wait for 2 minutes
            }
        }

        stage('Gracefully Stop Spring Boot App') {
            steps {
                script {
                    pipeline.stop_application()
                }
        }
    }
    
        stage('Cleaning') {
            steps {
                script {
                    pipeline.clean_up()
                }
        }
    }
