pipeline {
  agent any

  environment {
    JAVAREQV = '21.0.9'
  }

  stages {

    stage('build') {
      steps {
        script {
          def out = bat(script: 'java --version', returnStdout: true).trim()

          def m = (out =~ /openjdk\s+(\d+\.\d+\.\d+)/)
          if (!m.find()) {
            error("Could not extract Java version from:\n${out}")
          }

          env.SYSVERSION = m.group(1).trim()
          echo "Java version only: ${env.SYSVERSION}"
        }
      }
    }

    stage('test') {
      when {
        expression { env.SYSVERSION == env.JAVAREQV }
      }
      steps {
        echo 'both are same version'
      }
    }

    stage('mismatch') {
      when {
        expression { env.SYSVERSION != env.JAVAREQV }
      }
      steps {
        echo "Version mismatch. Required=${env.JAVAREQV}, Found=${env.SYSVERSION}"
        error("Failing build due to version mismatch")
      }
    }

  }
}
