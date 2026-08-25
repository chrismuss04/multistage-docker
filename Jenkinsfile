pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build image') {
            steps {
                // Runs Maven+JDK21 inside the build stage of the Dockerfile — no local mvn/JDK needed on the agent.
                sh 'docker build -t team-skeleton .'
            }
        }

        stage('Verify container starts') {
            steps {
                // Confirms the final runtime-stage image actually boots, not just that it builds.
                sh 'docker compose up -d'
                sh 'docker compose ps'
                sh 'docker compose down -v'
            }
        }
    }

    post {
        always {
            // Prevent the multi-stage build cache/layers from filling up the agent's disk over time.
            sh 'docker image prune -f'
        }
    }
}

