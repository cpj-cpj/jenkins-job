pipeline {
    agent any

    // No webhook required — poll GitHub for new commits every 5 minutes instead
    triggers {
        pollSCM('H/5 * * * *')
    }

    stages {

        stage('Build') {
            steps {
                echo "Task: Compile and package the source code so it is ready to be tested and deployed."
                echo "Tool: Maven"
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "Task: Run unit tests to check individual components, and integration tests to check that components work together correctly."
                echo "Tools: JUnit (unit tests), Selenium (integration tests)"
            }
        }

        stage('Code Analysis') {
            steps {
                echo "Task: Analyse the codebase for code smells, complexity, and adherence to coding standards."
                echo "Tool: SonarQube"
            }
        }

        stage('Security Scan') {
            steps {
                echo "Task: Scan source code and dependencies for known security vulnerabilities."
                echo "Tool: OWASP Dependency-Check"
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Task: Deploy the built application to a staging server that mirrors production for pre-release testing."
                echo "Tool: AWS EC2 (deployed via AWS CLI / Ansible)"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Task: Run integration tests against the staging environment to confirm the application behaves correctly in a production-like setting."
                echo "Tool: Postman / Newman"
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Task: Deploy the verified, tested application to the live production server."
                echo "Tool: AWS EC2 (deployed via AWS CLI / Ansible)"
            }
        }
    }
}
