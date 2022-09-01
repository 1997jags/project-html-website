#!groovy
pipeline {
  agent any
  stages
  {
    stage("install_nginx")
    {
      steps
      {
        script
        {
          sh 'sudo yum install nginx -y && sudo service nginx start'
        }
      }
    }
    stage("remove defaults") {
        steps {
            script {
            sh 'sudo rm -rf /usr/share/nginx/html/ '
            }
        }
    }
    stage("copy-test") {
        steps{
            script {
        sh 'sudo cp -r /var/lib/jenkins/workspace/multi_branch_test/* /usr/share/nginx/html/'
        sh 'sudo service nginx start'
        }
      }
    }
    stage("copy-master") {
        steps {
                script {
        sh 'sudo cp -r /var/lib/jenkins/workspace/multi_branch_master/* /usr/share/nginx/html/'
        sh 'sudo service nginx start'
        }
     }
    }

  }
}
