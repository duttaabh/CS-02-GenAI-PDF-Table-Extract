# README.md
##################################################################################################################################
# Pre-Requsites
1. python 3.9 or above
2. git cli (latest)
3. python libraries:
   * boto3
   * streamlit
   * streamlit_chat
   * langchain
   * amazon-textract-response-parser
   * amazon-textract-prettyprinter
   * amazon-textract-helper
   * faiss-cpu
   * opensearch-py
   * requests_aws4auth
##################################################################################################################################
# Run the Streamlit application in your local environment #
1. cd <LOCAL_DIR>
2. python -m venv env
3. source env/bin/activate
4. git clone https://github.com/duttaabh/CS-02-GenAI-PDF-Table-Extract.git
5. cd <LOCAL_DIR>/CS-02-GenAI-PDF-Table-Extract
6. pip install -r CS-02-GenAI-PDF-Table-Extract/requirements.txt
7. export AWS_REGION=<Application Deployment Region>
8. export S3_BUCKET_NAME=<S3 bucket for Textract PDF Analysis>
9. export OPENSEARCH_ENDPOINT=<Opensearch Endpoint URL to access the collections>
10. export DYNAMO_CHAT_HISTORY=<DynamoDB table name to store chat history>
11. Run python -m streamlit run main.py
12. The following prompt will appear upon execution of the previous command
  
  # You can now view your Streamlit app in your browser. #

  Network URL: http://xxx.xx.xx.xxx:8501
  External URL: http://x.xx.xx.xx:8501
################################################################################################################################## 
# Run the Streamlit application on EC2 with CloudFormation #
1. Download the streamlit_deploy.yaml file and create a new stack in AWS cloudformation console https://console.aws.amazon.com/cloudformation.
2. Please make sure to use your PC's public IP address in the CIDR input parameter (e.g. xx.xxx.xxx.xx/32) 
3. Once the CFN template is successfully running, please login to the EC2 instance created by the CFN
4. Please refer to the Stack output to find the instance id
5. Lookup the instance id in the EC2 clonsole (https://console.aws.amazon.com/ec2)
6. Use Session Mnagaer in the EC2 console to connect and open the EC2 terminal
7. Login as root (sudo su)
8. Then check the /var/log/cloud-init-output.log to see if the initialization scripts have successfully run (tail -100f /var/log/cloud-init-output.log)
9. Login as ec2-user and navigate to /home/ce2-user/ directory (sudo -i -u ec2-user)
10. Run ./set_env.sh to set the environment variables
11. Finally run "streamlit run main.py" to run the streamlit application
12. The following prompt will appear upon execution of the previous command
  
  # You can now view your Streamlit app in your browser. #

  Network URL: http://xxx.xx.xx.xxx:8501
  External URL: http://x.xx.xx.xx:8501
##################################################################################################################################
