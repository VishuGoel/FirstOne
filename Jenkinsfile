pipeline{
    agent none
    stages{
        stage('Non sequential stage'){
            agent{
                label 'master1'
            }
            steps{
                echo 'STAGE_NAME'
                script{
                    print(params.STAGE_NAME) //RETURNS null
                    print(env.STAGE_NAME)
                }
            }
        }
        stage('Sequential stage'){
            agent{
                label 'master1'
            }
            environment{
                sequential_param = 'practice sequential stage'
            }
            input{
                message 'It is a sequential stages practice session'
                ok 'OK'
            }
            stages{
                stage('Seq stage -1'){
                    steps{
                        print(env.STAGE_NAME)
                        print(env.sequential_param)
                    }
                }
                stage('Seq stage -2'){
                    steps{
                        print(env.STAGE_NAME)
                    }
                }
                stage('Parallel stages'){
                    /*options {
                        parallelsAlwaysFailFast()
                    }*/
                    failFast true
                    parallel{
                        stage('Parallel-1'){
                            steps{
                                print(env.STAG_NAME)
                            }
                        }
                        stage('Parallel-2'){
                            steps{
                                print(STAGE_NAME)
                            }
                        }
                    }//end of parallel
                }// end of parallel stage
            }//end of stages
        }
    }
}