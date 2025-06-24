pipeline{
    agent any
    
    tools{
        nodejs "node"
    }
    
    stages{
        stage("Clone Branch"){
            steps{
                git branch:"master", url:"https://github.com/Mumo-vicky/ip1week3.git"
            }
        }
        stage("Testing Pipeline"){
            steps{
                script{
                    echo "Testing..."
                }
            }
        }
        stage("Confirming dependencies installation"){
            steps{
                script{
                    echo "Installing dependencies..."
                    sh "npm install"
                }
            }
        }
        stage("Perform Test..."){
            steps{
                script{
                    echo "Perfoming npm test..."
                    sh "npm test"
                }
            }
        }
        stage("Deploying to Render"){
            steps{
                script{
                    def renderhook = "https://api.render.com/deploy/srv-d1cv0r95pdvs73c6qtmg?key=Fxd_U0WqR8A"
                    sh "curl -X POST ${renderhook}"
                    echo "Deployed to render"
                }
            }
        }
    }
    post {
        always {
            echo "Pipeline build succeded"
        }
        success {
            echo "Pipeline failed at some point! Sending notification email."
            mail to: 'vicky.mutua@student.moringaschool.com',
                 subject: "Jenkins Build FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: """
                 Hello Vicky,

                 The Jenkins pipeline build for '${env.JOB_NAME}' (Build #${env.BUILD_NUMBER}) has FAILED!

                 Build Status: ${currentBuild.result}
                 Triggered by: ${env.BUILD_CAUSE} (e.g., pushed code, manual trigger)

                 Please review the console output for details:
                 ${env.BUILD_URL}console

                 Best regards,
                 ipweek3pipeline
                 """
        }
    }
}