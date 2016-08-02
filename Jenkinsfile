node('dockerhost') {
    GIT_BRANCH = 'master'
    GIT_URL = 'git@github.com:Irdeto-Jenkins2/JenkinsDocker.git'

    def version = "${MAJOR}.${MINOR}.${PATCH}.${env.BUILD_NUMBER}"

    stage name: 'Build Docker Container'
    docker.build("jenkinsdocker:${version}")

    stage name: 'Deploy Docker Container'
    echo 'Not needed for demo :)'

    stage name: 'Update local Jenkins JobDSL'
    input ('JobDSL has been updated, do you want to proceed with updating local instance with these changes?')
    step([$class: ExecuteDslScripts, scriptLocation: [targets: 'artifacts/multiscreen-job.dsl'], ignoreExisting: false, lookupStrategy: 'JENKINS_ROOT', removedJobAction: 'DISABLE', removedViewAction: 'DELETE'])
}