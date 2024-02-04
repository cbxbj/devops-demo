pipeline{
  // 任何一个代理可用就可以执行
  agent any

  // 定义一些环境信息
  environment {
    hello = "123"
    cicd = "456"
  }

  // 定义流水线的加工流程
  stages{
    // 流水线的所有阶段
    stage('环境检查'){
      steps{
        sh 'printenv'
        sh 'java -version'
        sh 'git --version'
        sh 'docker version'
        sh 'mvn -v'
      }
    }
    // 1、编译
    stage('编译'){
      steps{
        // 要做的所有事情
         echo "编译..."
         echo "$hello"
         echo "${cicd}"
         sh 'pwd && ls -alh'
         sh 'printenv'
      }
    }

    // 2、测试
    stage('测试'){
      steps{
        // 要做的所有事情
        echo "测试..."
      }
    }

    // 3、打包
    stage('打包'){
      steps{
        // 要做的所有事情
        echo "打包..."
      }
    }

    // 4、部署
    stage('部署'){
      steps{
        // 要做的所有事情
        echo "部署..."
      }
    }
  }



}