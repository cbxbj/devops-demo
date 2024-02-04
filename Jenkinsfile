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
        sh 'pwd && ls -alh'
        // 取环境变量值都用双引号
        sh "echo $hello"
        sh "echo ${cicd}"
        //sh 'mvn -v'
      }
    }

    // 1、编译
    stage('编译'){
      agent {
        docker { image 'maven:3.9.6-eclipse-temurin-17-alpine' }
      }
      steps{
         sh 'pwd && ls -alh'
         sh 'mvn -v'
         sh 'cd /var/jenkins_home && ls -alh'
         // 打包 --> .jar 使用阿里云
         sh 'mvn clean package -s "/var/jenkins_home/appconfig/maven/settings.xml"  -Dmaven.test.skip=true'
      }
    }

    // 2、测试
    stage('测试'){
      steps{
        echo "测试..."
      }
    }

    // 3、生成镜像
    stage('生成镜像'){
      steps{
        echo "生成镜像..."
        sh 'docker version'
        sh 'pwd && ls -alh'
      }
    }

    // 4、部署
    stage('部署'){
      steps{
        echo "部署..."
      }
    }

  }

}