# streamlit-on-openshift
Deploying a Streamlit app on OpenShift

## Prerequisites

- OpenShift Access
- a Development environment with the following tools installed:
  - Git
  - Python
    - Streamlit


## Steps to Deploy a Streamlit App on OpenShift using s2i
1. Create a Streamlit App or use an existing one
2. Add a `requirements.txt` file with the app's dependencies
3. Add a `.s2i/bin/run` file with the following content:
```bash
APP_PORT=${APP_PORT:-"8080"}
streamlit run --server.port ${APP_PORT} app.py
```
4. Create a new OpenShift project or use an existing one
5. From the OpenShift Web Console ("Developer" view, not Administrator), select the project you want to deploy the app into
6. Click the '+Add' option on the left-hand menu and select 'Import from Git'
7. Provide your Git repository's 'clone' URL. After the URL is validated, click 'Create' (accept the default options for the form that appears)
8. Wait for the build to complete and the app to be deployed
9. Access the app by clicking on the route that is created for the app

## Video Demo
![Streamlit on OpenShift](media/deploying_streamlit_with_s2i.mov)

## Steps to enable Web Hooks for automatic deployment
1. Go to the OpenShift console
2. Click on your application
3. Under the "Builds" section, click on the "Build Config" link
4. At the bottom of the Build Config page, click on the "Copy URL" link
5. Go to your GitHub repository
6. Click on the "Settings" tab
7. Click on the "Webhooks" link
8. Click on the "Add webhook" button
9. Paste the URL you copied from the OpenShift console into the "Payload URL" field
10. Set the "Content type" to "application/json"
11. Click on the "Add webhook" button

## Links to resources used during this workshop
- ![Streamlit](https://streamlit.io/)
- ![Streamlit on OpenShift](https://github.com/redhat-na-ssa/streamlit-on-openshift)
  - Borrowed from: ![Streamlit Cheat Sheet](https://github.com/daniellewisdl/streamlit-cheat-sheet)
- 
