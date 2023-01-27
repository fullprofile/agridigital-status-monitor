# AgriDigital Status Monitor

This repository contains the open-source uptime monitor and status page for [AgriDigital](https://app.agridigital.io), powered by [Upptime](https://github.com/upptime/upptime).
[📈 AgriDigital Status Monitor](https://fullprofile.github.io/agridigital-status-monitor) provides a quick look at our Agridigital services and the uptime of each service. It is a public status monitor website. It shows Agridigital websites' live status, incident history, and response time graphs.

## Getting Started

These instructions will guide you on how to create a status monitor page and running on your local machine for development and testing purposes.
**See Issue & Banner for notes on creating notices on status monitor page.**

### Prerequisites

Requirements for the software and other tools to build, test and push

- [Visual Studio Community](https://visualstudio.microsoft.com/downloads/)
- Slack Channel

### Development

#### Create a repository from the template

- On GitHub, navigate to the main page of the repository - GitHub - upptime/upptime: ⬆️ Free uptime monitor and status page powered by GitHub
- Above the file list, click Use this template.
- Use the Owner drop-down menu, and select the account you want to own the repository.
- Type a name for your repository, and an optional description.
- Choose a repository visibility as Public
- Important: Check "Include all branches"
- Click Create repository from template
- Your status page will be hosted on https://<user>.github.io/<repo> where user is your GitHub username and repo is your repository name.

#### Enable Publishing in Github

- Go to your repository settings page
- Go to the "Pages" sub-section on the left
- Under "Source", change "None" to gh-pages
- In the folder dropdown, select /(root)
- Enter the Custom domain
- Click on "Save"

#### Add repository secrets

- Click on your profile picture on the top-right corner and select "Settings"
- In the left sidebar, select "Developer settings"
- In the left sidebar, click "Personal access tokens"
- Click "Generate new token"
- Select the "repo" and "workflow" scopes
- Click "Generate token"
- After generating your token, copy it (you will not see it again). Then, add it as a repository secret:
- In your Upptime repository, select "Settings"
- In the left sidebar, click "Secrets"
- Press the button "New repository secret"
- Enter the name of the secret as GH_PAT
- Paste your personal access token into the Value field
- Be sure there are no spaces before or after the token and/or linebreaks after your token
- Save your PAT by selecting "Add secret"

#### Create custom name in Route53 in AWS

- Create a custom name in AWS (Route 53)

#### Update Configuration in repo

- Verify owner (organization or username, where this repository lives) and repo ( name of this repository) in in .upptimerc.yml configuration file.
- Enter the endpoints you want to monitor in .upptimerc.yml configuration file.
- You can start by adding your endpoints under sites:
- To use a custom domain, remove the line starting with baseUrl: and instead add your custom domain name in cname:
- To customise the page follow configuration mentioned in Configuration | Upptime
- Push your changes to master repository

#### Enable HTTPS in Github Pages

- Go to your repository settings page
- Go to the "Pages" sub-section on the left
- Check the box for Enforce HTTPS
- Click on "Save"

#### Add Slack notification

- Create slack channel for tracking status for agridigital status monitor
- Create slack app and a slack webhook URL. See the article https://slack.com/intl/en-in/help/articles/115005265063-Incoming-webhooks-for-Slack for Slack on the Slack website.
- Create additional environment variables in Repository secrets
  NOTIFICATION_SLACK Set to true
  NOTIFICATION_SLACK_WEBHOOK Set to true
  NOTIFICATION_SLACK_WEBHOOK_URL Slack webhook URL

### Deployment

A step by step to track sites/endpoints in status monitor page

Clone Repository

    git clone https://github.com/fullprofile/agridigital-status-monitor.git

- Open in Visual Studio
- Open .upptimerc.yml file. The .upptimerc.yml file is used as the central configuration for Upptime, with this syntax
- After you've created a new repository using this template, specify the username and repository name in the configuration
- You can track as many websites as you like. Add the names and URLs of your endpoints in the sites key

```
sites:

  - name: Google
    url: https://www.google.com
  - name: DuckDuckGo
    url: https://duckduckgo.com
```

- Maximum response time - Upptime endpoints can be up, down, or degraded. By default, if an endpoint takes more than 30 seconds to respond, its performance is tracked as "degraded". You can customize the maximum response time. In the below example, this endpoint will be measured as degraded if it takes more than 5 seconds to respond.
```
  - name: Slow endpoint
    url: https://example.com
    maxResponseTime: 5000
```
- Custom domain: To use a custom domain, add the cname key
```
  status-website:
  name: Upptime
  logoUrl: https://example.com/image.jpg
  cname: status.agridigital.io # Custom CNAME
```
- See detailed configuration settings in https://upptime.js.org/docs/configuration

### How it works

- GitHub Actions is used as an uptime monitor
- Every 5 minutes, a workflow visits your website to make sure it's up
- Response time is recorded every 6 hours and committed to git
- Graphs of response time are generated every day
- GitHub Issues is used for incident reports
- An issue is opened if an endpoint is down
- Incidents reports are posted as issue comments
- Issues are closed automatically when your site comes back up
- Slack notifications are sent on updates

## Issue & Banner

### Create Notice/issue on status monitor page

- Go to Agridigital [Status monitor repo](https://github.com/fullprofile/agridigital-status-monitor/issues)
- Create new label - status with description - issue in github repository
- Click on button 'Create new issue'
- Add status label
- Add issue title (Title is displayed on the top of the status monitor page)
- Submit new issue
- Add a new comment to add description. It will display in incident detail page of status monitor page
- Incident is created on status monitor page

### Close Issue on AgriDigital platform

- Navigate to the issue that you want to close Agridigital [Status monitor repo](https://github.com/fullprofile/agridigital-status-monitor/issues)
- Enter the closing comment and click Close with comment button
- The public status page gets updated and closed notices are pushed to the bottom.

### Add banner on AgriDigital platform

- Go to Agridigital [Status monitor repo](https://github.com/fullprofile/agridigital-status-monitor/issues)
- No label required
- Click on button 'Create new issue'
- Add Title. (Title is not displayed in the banner section)
- In comment section, Enter the banner message you want to display in the platform. Add the complete message to be displayed on the banner, including the header
- Submit new issue
- This will create issue on [agridigital] (https://github.com/fullprofile/agridigital) repo that triggers the activation of the banner using the message entered on the issue body.

### Remove banner on AgriDigital platform

- Navigate to the issue that you want to close Agridigital [Status monitor repo](https://github.com/fullprofile/agridigital-status-monitor/issues)
- Enter the closing comment and click Close with comment button
- Closing the issue will close the related issue on agridigital repo which will deactivate the banner on AD1

## Authors

- AgriDigital (Full Profile Pty Ltd)

See also the list of contributing team members:

- Upptime Bot
- Shilpa Gupta
- Reden
- Nick Cooney

## License

- Powered by: [Upptime](https://github.com/upptime/upptime)
- Code: [MIT](./LICENSE) © [AgriDigital](agridigital.io)
- Data in the `./history` directory: [Open Database License](https://opendatacommons.org/licenses/odbl/1-0/)

## Acknowledgments

- Powered by Upptime : https://github.com/upptime/upptime
