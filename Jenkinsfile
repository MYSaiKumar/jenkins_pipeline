pipeline {
agent any 
environment {javareqV='21.0.9'}

stages{

<<<<<<< HEAD
stage ('build')
{
=======
        stage('Build') {
            steps {
                echo 'Building the application'
                bat 'java --version'
            }
        }
>>>>>>> bc83e8246ec336e4239704fd2f557a959d64e20b

steps {
bat 'java --version'

script {
  def out = bat(script: 'java --version', returnStdout: true).trim()

  def m = (out =~ /openjdk\s+(\d+\.\d+\.\d+)/)
  if (!m.find()) {
    error("Could not extract Java version from:\n${out}")
  }

  def sysVersion = m.group(1).trim()
  echo "Java version only: ${sysVersion}"

  env.SYSVERSION = sysVersion
}

}

stage ('test')
//when sysversion == javareqV
when {expression{env.SYSVERSION == env.javareqV}}
step{
{

echo 'both are same verson'
}

}

}



}