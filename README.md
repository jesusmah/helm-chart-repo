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
