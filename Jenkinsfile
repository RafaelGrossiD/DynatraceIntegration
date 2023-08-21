 def dyna_json = """
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
}
"""

def dyna_request = httpRequest contentType: 'APPLICATION_JSON', customHeaders: [[value: "Api-Token ${env.DT_API_TOKEN}"]], httpMode: 'POST', requestBody: dyna_json, responseHandle: 'STRING', url: "${env.DT_TENANT_URL}api/v2/events/ingest", validResponseCodes: "100:404"
