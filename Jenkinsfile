@Library("dynatrace@events-v2")
def event = new com.dynatrace.ace.Event()

def tagMatchRules = [[
  "meTypes": [ "PROCESS_GROUP_INSTANCE"],
  tags: [
    ["context": "CONTEXTLESS", "key": "Jenkins"],
    ["context": "CONTEXTLESS", "key": "AWS"]
  ]
]]

pipeline {
    agent any
    environment {
      DT_TENANT_URL = credentials('DT_TENANT_URL')
    	DT_API_TOKEN = credentials('DT_API_TOKEN')
    }
    stages {
        stage("CUSTOM_DEPLOYMENT") {
            steps {
                script {
                    def status = event.pushDynatraceEvent (
                      eventType: "CUSTOM_DEPLOYMENT",
                      tagRule: tagMatchRules,
                      deploymentName: "CUSTOM_DEPLOYMENT: ${env.JOB_NAME}",
                      deploymentVersion: "v0.1",
                      deploymentProject: "TestJenkinsDynaIntegration",
                      remediationAction: "myRemediationAction",
                      customProperties : [
                          "Jenkins JOB_NAME": "${env.JOB_NAME}",
                          "Jenkins BUILD_NUMBER": "${env.BUILD_NUMBER}"
                      ]
                    )
                  }
            }
        }
                                        
    }
}
