node {
       
    stage "CheckoutCode"
    
    checkout scm
    
    stage "PrepreAndroidEnv"
    
    sh "pwd && ls"      
      
    sh "docker images | grep mingc/android-build-box"   
    
    stage "BuildAndroidPorject"
    
    sh "docker run --rm -v /root/.jenkins/workspace/android-docker-build-demo:/project mingc/android-build-box bash -c 'cd /project; ./gradlew build'" 
        
    stage "Archive"

    sh "cp '$PWD'/project/*.apk /ProjectName/bin/Release/"

    stage "Deploy"
    
    sh ""

}
