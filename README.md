# streamlit-on-openshift
Deploying a Streamlit app on OpenShift

## Prerequisites

- OpenShift Access


## Steps to Deploy a Streamlit App on OpenShift using s2i
1. Create a Streamlit App or use an existing one
2. Add a `requirements.txt` file with the app's dependencies
3. Add a `.s2i/bin/run` file with the following content:
```bash
APP_PORT=${APP_PORT:-"8080"}
streamlit run --server.port ${APP_PORT} app.py
```
4. Create a new OpenShift project or use an existing one
5. From the OpenShift Web Console, select the project you want to deploy the app into
6. Click the '+Add' option on the left-hand menu and select 'Import from Git'
7. Provide your Git repository's 'clone' URL. After the URL is validated, click 'Create' (accept the default options for the form that appears)
8. Wait for the build to complete and the app to be deployed
9. Access the app by clicking on the route that is created for the app

## Video Demo
![Streamlit on OpenShift](media/deploying_streamlit_with_s2i.mov)
