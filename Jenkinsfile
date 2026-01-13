pipeline {
agent any 
environment {javareqV='21.0.9'}

stages{

stage ('build')
{

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