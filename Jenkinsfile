pipeline {
  agent any
  stages {
    stage('CodeQL Scan') {
      environment {
        GITHUB_CREDS = credentials('pat-that-may-work')
      }
      steps {
        sh '''ls -lah
commit_id=`git rev-parse HEAD`
echo " COMMIT ID is $commit_id"
refs_value=`git symbolic-ref HEAD`
echo "REF is $refs_value"
/var/lib/codeql-utilities/codeql-runner-linux init --repository rohitdemo/codeql-testing --github-url https://github.com --github-auth $GITHUB_CREDS_PSW
/var/lib/codeql-utilities/codeql-runner-linux analyze --repository rohitdemo/codeql-testing --github-url https://github.com --github-auth $GITHUB_CREDS_PSW --commit $commit_id --ref $refs_value '''
      }
    }

  }
}