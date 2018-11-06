#!/usr/bin/groovy

@Library('github.com/sbose78/osio-pipeline@master') _

osio {

  config runtime: 'golang'

  ci {
     // override the RELEASE_VERSION template parameter
    def resources = processTemplate(params: [
        RELEASE_VERSION: "1.0.${env.BUILD_NUMBER}"
    ])
    
    // performs an s2i build
    build resources: resources    
    
    deploy resources: resources, env: 'stage' 

  }

  cd {

    // override the RELEASE_VERSION template parameter
    def resources = processTemplate(params: [
        RELEASE_VERSION: "1.0.${env.BUILD_NUMBER}"
    ])

     // performs an s2i build
    build resources: resources
    
    deploy resources: resources, env: 'stage' 
    deploy resources: resources, env: 'run', approval: 'manual'
  }
}
