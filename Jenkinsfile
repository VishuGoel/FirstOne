pipeline{
    agent any
    stages{
        stage('Non sequential stage'){
            steps{
                echo 'STAGE_NAME'
                script{
                    print(params.STAGE_NAME) //RETURNS null
                    print(env.STAGE_NAME)
                }
            }
        }
    }
}