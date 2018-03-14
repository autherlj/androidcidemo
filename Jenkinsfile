node {
       
    stage "CheckoutCode"
    
    checkout scm
    
    stage "PrepreAndroidEnv"
    
    sh "pwd && ls"      
      
    sh "docker images | grep mingc/android-build-box"
       
    sh "echo 'sdk.dir=/opt/android-sdk' > local.properties"   
    
    stage "BuildAndroidPorject"
    
    sh "docker run --rm -v /jenkins/workspace/android-docker-build-demo:/project mingc/android-build-box bash -c 'cd /project; ./gradlew build'" 
        
    stage "Archive"

    sh "echo '3'"

    stage "Deploy"
    
    sh "ehco '4'"

}
