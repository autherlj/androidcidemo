node {
       
    stage "CheckoutCode"
    
    checkout scm
    
    stage "CheckAndroidBuildStatus"
    
    sh "echo '$PWD'"
    
    sh "ls && mkdir project"
       
    sh "cp ./* ./project"
      
    sh "docker images"   
    
    stage "BuildAndroidPorject"
    
    sh "docker run --rm -v '$PWD'/project:/project mingc/android-build-box bash -c 'cd /project; ./gradlew build'" 
        
    stage "Archive"

    sh "cp '$PWD'/project/*.apk /ProjectName/bin/Release/"

    stage "Deploy"
    
    sh ""

}
