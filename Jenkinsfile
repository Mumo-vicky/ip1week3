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
}