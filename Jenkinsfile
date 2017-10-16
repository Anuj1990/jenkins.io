#!/usr/bin/env groovy
import hudson.model.AbstractProject
import hudson.tasks.Mailer
import hudson.model.User

@NonCPS
def getJobemail() {
    def user = hudson.model.User.current();
    string emailid = user.getProperty(hudson.tasks.Mailer.UserProperty.class).getAddress();
    return user.getProperty().getAddress();
    //return emailid;
}

    node('master') {
        stage('Clean workspace') {
            /* Running on a fresh Docker instance makes this redundant, but just in
            * case the host isn't configured to give us a new Docker image for every
            * build, make sure we clean things before we do anything
            */
            deleteDir()
            sh 'ls -lah'
        }


        stage('Checkout source') {
            /*
            * For a standalone workflow script, we would use the `git` step
            *
            *
            * git url: 'git://github.com/jenkinsci/jenkins.io',
            *     branch: 'master'
            */

            /*
            * Represents the SCM configuration in a "Workflow from SCM" project build. Use checkout
            * scm to check out sources matching Jenkinsfile with the SCM details from
            * the build that is executing this Jenkinsfile.
            *
            * when not in multibranch: https://issues.jenkins-ci.org/browse/JENKINS-31386
            */
            //checkout scm
        }


        stage('sendNotification') {
         
           string email = getJobemail();
            echo email;
    
    String recipient = 'anuj_sharma401@yahoo.com'

    mail subject: "${env.JOB_NAME} (${env.BUILD_NUMBER}) failed",
            body: "It appears that ${env.BUILD_URL} is failing, somebody should do something about that",
              to: recipient,
         replyTo: recipient,
            from: 'noreply@ci.jenkins.io'

        }
}
