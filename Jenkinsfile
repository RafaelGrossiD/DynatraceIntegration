pipeline {
    agent any
    environment {
      DT_TENANT_URL = credentials('DT_TENANT_URL')
    	DT_API_TOKEN = credentials('DT_API_TOKEN')
    }
stage('Execute Request') {
      steps {
         script {
				sh "curl -X 'POST' \
		  '${DT_TENANT_URL}api/v2/events/ingest' \
		  -H 'accept: application/json; charset=utf-8' \
		  -H 'Authorization: Api-Token ${DT_API_TOKEN}' \
		  -H 'Content-Type: application/json; charset=utf-8' \
		  {
		  "title" : "Easytravel",
		  "eventType": "CUSTOM_DEPLOYMENT",
		  "entitySelector": "type(process_group_instance),tag(Jenkins)",
		  "properties": {
		    "dt.event.deployment.name": "Easytravel",
		    "dt.event.deployment.project": "Project X",
		    "dt.event.deployment.remediation_action_link": "https://url",
		    "dt.event.deployment.version": "4.0",
		    "dt.event.deployment.release_stage": "prd", 
		    "dt.event.deployment.release_product": "easytravel frontend - CoachingSession"
		   }
		}'
		"
            }
      }
 }
}	
