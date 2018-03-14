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
               sh "docker run --rm -v /jenkins/workspace/android-docker-build-demo:/project android-build-box bash -c 'cd /project; ./gradlew build'"
               sh "cd /jenkins/workspace/android-docker-build-demo/app/build/outputs && tree ./apk"
           }
      
       }catch(error)
       {
              currentBuild.result = "FAILURE"
              throw error       
       }  
}
