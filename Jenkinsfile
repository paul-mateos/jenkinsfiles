node('VB_JenkinsSlave_DockerEngine'){
    
    stage("Clone Repo")
    checkout([$class: 'GitSCM', branches: [[name: '*/master']], browser: [$class: 'GithubWeb', repoUrl: 'git@github.com:paul-mateos/docker_hello-world.git'], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CloneOption', noTags: false, reference: '', shallow: true]], gitTool: 'LinuxGit', submoduleCfg: [], userRemoteConfigs: [[credentialsId: '77fb1cb8-ee14-4226-9b1e-38d014f21261', url: 'git@github.com:paul-mateos/docker_hello-world.git']]])
    
    stage("Build Docker files")
    db = docker.build('docker_hello-world', '.')
    
    stage("Push to Registry")
    docker.withRegistry('https://192.168.139.2:5000') {
          db.push()
      }
    
    
}
