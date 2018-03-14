node{
              currentBuild.result = "SUCCESS"  
    try{
           stage ('CheckoutCode'){
              checkout scm       
           }
           stage ('PrepreAndroidEnv'){
               sh "pwd && ls"      
               sh "docker images | grep android-build-box"
               sh "echo 'sdk.dir=/opt/android-sdk' > local.properties" 
           }
           stage ('BuildAndroidPorject'){
               sh "docker run --rm -v /jenkins/workspace/android-docker-build-demo:/project android-build-box bash -c 'cd /project; ./gradlew assembleDebug'"
               sh "cd app/build/outputs/ && tree ./apk"
           }
           stage('DeploytoHockeyapp'){
               step([$class: 'HockeyappRecorder', applications: [[apiToken: '32387bb0293546d0935a0c2041dbff7e', downloadAllowed: true, 
                    filePath: 'app/build/outputs/apk/release/app-release-unsigned.apk', 
                    mandatory: false, notifyTeam: false, releaseNotesMethod: [$class: 'NoReleaseNotes'], 
                    uploadMethod: [$class: 'AppCreation', publicPage: false]]], debugMode: false, failGracefully: false])
           }
      
       }catch(error)
       {
              currentBuild.result = "FAILURE"
              throw error       
       }  
}
