# helm-chart-repo

Create a personal Helm repository using a Github repo
- Create a new github repository
- Go to Settings > Pages tab
- Under "Source", select the main branch and save.
- Your repository should now have a public URL -> https://<git-org>.github.io/<repo-name>/


1. Create a template helm chart

   ```bash
   helm create <chart-name>
   ```

2. Lint the chart 

   ```bash
   helm lint .
   ```

3. Generate yaml from the chart 

   ```bash
   helm template .
   ```

4. Generate a tgz of your helm chart 

   ```bash
   helm package <chart-name>
   ```

5. Generate / update index.yaml for your Helm repository 
	
   ```bash
   helm repo index --url <helm-repo-url> .
   ```

6. Add a Helm repository locally mq
	
   ```bash
   helm repo add <helm-repo-name> <helm-repo-url: not GitHub repo instead use github pages repo url>
   ```

7. Refresh contents of remote Helm repositories

   ```bash
   helm repo update
   ```

8. Search for charts available in a Helm repository

   ```bash
   helm search repo <helm-repo-name>
   ```

_Example_

- Updated `ibm-catalogs` helm chart
- Created new `ibm-common-services`, `ibm-common-services-instance`, `ibm-eventstreams-instance`, `ibm-eventstreams-operator` helm charts

After doing all changes in VSCode, I executed the following:

```bash
~/Workspace/GitHub/jesusmah/PROD/helm-chart-repo $ helm package ibm-common-services
~/Workspace/GitHub/jesusmah/PROD/helm-chart-repo $ helm package ibm-common-services-instance
~/Workspace/GitHub/jesusmah/PROD/helm-chart-repo $ helm package ibm-eventstreams-instance
~/Workspace/GitHub/jesusmah/PROD/helm-chart-repo $ helm package ibm-eventstreams-operator
```

that corresponds to: `4. Generate a tgz of your helm chart`

Commit changes to GitHub

```bash
~/Workspace/GitHub/jesusmah/PROD/helm-chart-repo $ git add --all
~/Workspace/GitHub/jesusmah/PROD/helm-chart-repo $ git commit -s -m "New helm chart packages"
~/Workspace/GitHub/jesusmah/PROD/helm-chart-repo $ git push origin main
```

Then,

```bash
~/Workspace/GitHub/jesusmah/PROD/helm-chart-repo $ helm repo index --url https://jesusmah.github.io/helm-chart-repo/ .
```

that corresponds to: `5. Generate / update index.yaml for your Helm repository`

Commit changes to GitHub

```bash
~/Workspace/GitHub/jesusmah/PROD/helm-chart-repo $ git add --all
~/Workspace/GitHub/jesusmah/PROD/helm-chart-repo $ git commit -s -m "updating helm repo index"
~/Workspace/GitHub/jesusmah/PROD/helm-chart-repo $ git push origin main
```

Finally,

```bash
~/Workspace/GitHub/jesusmah/PROD/helm-chart-repo $ helm repo update
```

that corresponds to: `7. Refresh contents of remote Helm repositories`

And,

```bash
~/Workspace/GitHub/jesusmah/PROD/helm-chart-repo $ helm search repo personal -l
```

that corresponds to: `8. Search for charts available in a Helm repository`
(`-l` to list all versions)

You can find the name of the local repositories by executing:

```bash
~/Workspace/GitHub/jesusmah/PROD/helm-chart-repo $ helm repo list
```
