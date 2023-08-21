@Library("dynatrace@events-v2")
def event = new com.dynatrace.ace.Event()

def selector = "type(PROCESS_GROUP_INSTANCE),tag(Jenkins)"

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
		      title: "New Deployment",
                      entitySelector: selector,
                      properties: [
			  "dt.event.deployment.version": "1.1",
                          "dt.event.deployment.release_stage": "production",
                          "dt.event.deployment.release_product": "frontend",
                          "dt.event.deployment.release_build_version": "123",
                          "approver": "<responsible Team/Person>",
                          "dt.event.deployment.ci_back_link": "https://pipelines/easytravel/123",
                          "gitcommit": "<git-commit-id>",
                          "change-request": "<Change-Request-ID>"
		      ]
                    )
                  }
            }
        }
                                        
    }
}
