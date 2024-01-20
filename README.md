## Create bitbucket repo with ansible

The objective of this playbook was automate the creation fo repositories in bitbucket cloud, based in the bitbucket rest api with curl requests and ansible web server calls.

The repository created contain webhooks, upload content like files, branch names and branch model. In every task of the playbook i added a description of the action to execute by ansible. Aditional to this, the playbook use environment variables to simplify the execution of the playbook, or for much iterations.

### To execute the playbook
```
ansible-playbook playbook-create-repo-bitbucket.yaml
```
You don't need to add an inventory file for this execution. First you use your local machine for execute ansible, and all the task are web server calls. The idea was not depend for a language and base in curl, as same in the bitbucket rest api examples.

### Environment Variables

- **repository_name**: name of the repository 
- **workspace**: https://developer.atlassian.com/cloud/bitbucket/rest/api-group-workspaces/#api-group-workspaces
- **project_key**: the key of the project where the repository belongs
- **prod_branch**: the name of production branch, my case master, maybe yours main or what ever you want
- **qa_branch**: this branch is pre production branch, my case qa, maybe yours release or staging
- **dev_branch**: the name of development branch
- **auth_token**: the token you need to execute every task against the bitbucket rest api. In this section you can define a Bearer token or Basic token with the account name and the password in base 64.

### Samples token

- **Bearer token**
```
Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c3VhcmlvIjoidXNlcm5hbWUifQ.ppwldKJ0pNCWrZUeMIPYtDgw-WebVQ-50_JL9KHoHNA
```

- **Basic token** (username=fillanes/ password=123123123)
```
fillanes:123123123 in Base64
Basic ZmlsbGFuZXM6MTIzMTIzMTIz
```
