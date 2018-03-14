node {
    
    checkout scm
    
    stage "CheckoutCode"
    
    sh "echo $PWD && ls"
    
    stage "CheckAndroidBuildStatus"
    
    sh "docker images | grep mingc/android-build-box"
    
    stage "BuildAndroidPorject"
    
    sh "docker run --rm -v '$PWD'/project:/project mingc/android-build-box bash -c 'cd /project; ./gradlew build'" 
        
    stage "Archive"

    sh "cp '$PWD'/project/*.apk /ProjectName/bin/Release/"

    stage "Deploy"
    
    sh ""

}
