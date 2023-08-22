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
def dyna_json = """
{
  "title" : "PetClinic",
  "eventType": "CUSTOM_DEPLOYMENT",
  "entitySelector": "type(process_group_instance),tag(Jenkins)",
  "properties": {
   // "Jenkins JOB_NAME": "${env.JOB_NAME}",
   // "Jenkins BUILD_NUMBER": "${env.BUILD_NUMBER}"
   // "dt.event.deployment.name":"${env.JOB_NAME}",
    "dt.event.deployment.project": "Project CICD",
    "dt.event.deployment.remediation_action_link": "https://urlexample",
    "dt.event.deployment.version": "5.0",
    "dt.event.deployment.release_stage": "PRD", 
    "dt.event.deployment.release_product": "PetClinic Web page"
   }
}
"""

def dyna_request = httpRequest contentType: 'APPLICATION_JSON', customHeaders: [[maskValue: false, name: 'Authorization', value: "${env.DT_API_TOKEN}"]], httpMode: 'POST', requestBody: dyna_json, responseHandle: 'STRING', url: "${env.DT_TENANT_URL}", validResponseCodes: "100:404"
                  }
            }
        }
                                        
    }
}    


