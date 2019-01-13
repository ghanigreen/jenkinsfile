node {
    stage ("scm")
    {
    git 'https://github.com/ghanigreen/maven_demo.git'
    }
    stage ("build")
    {
    bat 'mvn package'
    }
    stage ("sonar")
    {
    bat 'mvn sonar:sonar'   
    }
    stage ("artifactory")
    archiveArtifacts '**/*.war'
    stage ("Unittesting")
     junit '**\\gameoflife-web\\target\\surefire-reports\\*.xml'
     stage ("analysis")
     {
              timeout(time: 1, unit: 'HOURS') {
                waitForQualityGate abortPipeline: true
              }
    }
    stage ("deploy")
    {
        sh 'cp -R "C:\\Users\\Lap GT Adayar 10\\.jenkins\\workspace\\mavenpipeline\\gameoflife-web\\target\\gameoflife.war" "C:\\Program Files\\Apache Software Foundation\\Tomcat 9.0\\webapps"'
    }

    
    
}
