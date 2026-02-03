# Rover Medical System

A demonstration of how to apply the Assured Release approach in small slices over time.

## Demo Setup

The five steps to set up and do one crank of the demo are as follows:

1. Create a Detached Clone of the Attestify Rover Medical System
2. Enable GitHub Actions in this new Detached Clone
3. Create a Branch for a Release Update
4. Make a Release Update
5. Merge Updates and Execute Verification Procedure

The below directions guide you on how to setup and execute the demo within the GitHub website. There is nothing stopping you from doing this in an IDE and with the CLI tools.

### 1. Create a Detached Clone of the Attestify Rover Medical System

1. To import a new repository, click on the following link: [Import a repository](https://github.com/new/import), or
2. You will be asked for the URL for the source repository, provide `https://github.com/attestify/rover-medical-system.git`
3. For the repository name, we suggest keeping `rover-medical-system`
4. **NOTE**
    1. There is no need for a username or an access token/password for this repository, as attestify/rover-medical-system is public.
    2. Make sure to select "public" for this new repo you are creating; we do not support this demo with "private" repos.
5. When import is complete (it can take a few minutes), you'll now have the Rover Medical System repo at: `https://github.com/[your-organization]/rover-medical-system.git

### 2. Enable GitHub Actions in this new Detached Clone

1. Navigate to the "Actions" and click the button that says, "Enable Actions on this Repository."

### 3. Create a Branch for a Release Update

1. Click on the "Branch" button in the repo.
2. In the branch view, click on the "New branch" button at the top right
3. Give it a name (e.g., "R1-to-R2")
4. Ensure the "Source" is the main branch
5. Click "Create new branch."

### 4. Make a Release Update
   1. Navigate to the branch dropdown (top left), which most likely says "main."
   2. Click that dropdown, and click the branch name you created
   3. To verify you are on that branch, where it said "main", it will now say your branch name (e.g., "R2-to-R1")
   4. Edit Files
      1. Update the `RELEASE` file with the number of the release you want the demo to demonstrate
      2. Update the s`ystem-cicd.yml` file using the directions provided below for the release you are targeting to demo.

### 5. Merge Updates and Execute Verification Procedure

1. Generate a pull request.
2. Do a "Squash and Merge"
3. Once merged, go to the "Actions" tab to see the verification process execute.
4. When done, select the saved output called "rover-medical-system-release-[number]" where the number is the release number you chose to demo.

For repetitive turns-of-the-demo-crank, simply update the `RELEASE` file with the release number of either "1", "2", "3", "4", and update the `system-cicd.yaml` with the below NAPE CLI evidence collection commands given the release

## The Releases


### Release 1

Ensure that after the ```nape start collect ...``` command, the below ```nape collect evidence ...``` is the only command that exists in the [systems-cicd.yml](.github/workflows/system-cicd.yml):

**RELEASE**
```text
1
```

**system-cicd.yml**
```bash
          echo "--- Release 1 - Evidence Collection --- "

          nape collect evidence \
            --control-activity "pet-medicine-app" \
            --file-path "pet-medicine-app/app-config.toml"
```
____

### Release 2

Add the below ``nape collect evidence ...``` command after the Release 1 command

**RELEASE**
```text
2
```

**system-cicd.yml**
```bash
          echo "--- Release 2 - Evidence Collection (Additions) --- "

          nape collect evidence \
            --control-activity "pet-medicine-db" \
            --file-path "pet-medicine-db/my-db.ini"

```
____

### Release 3

Add the below ``nape collect evidence ...``` commands after the Release 2 command

**RELEASE**
```text
3
```

**system-cicd.yml**
```bash
          echo "--- Release 3 - Evidence Collection (Additions) --- "

          nape collect evidence \
          --control-activity "pet-medicine-host" \
          --file-path "pet-medicine-host/stdout-auditctl-installed.txt"

          nape collect evidence \
          --control-activity "pet-medicine-host" \
          --file-path "pet-medicine-host/stdout-auditctl-user-commands-logged.txt"

          nape collect evidence \
          --control-activity "pet-medicine-host" \
          --file-path "pet-medicine-host/stdout-no-login-app-user.txt"

          nape collect evidence \
          --control-activity "pet-medicine-host" \
          --file-path "pet-medicine-host/stdout-no-login-db-user.txt"

          nape collect evidence \
          --control-activity "pet-medicine-host" \
          --file-path "pet-medicine-host/stdout-root-check-admin-user.txt"

          nape collect evidence \
          --control-activity "pet-medicine-host" \
          --file-path "pet-medicine-host/stdout-root-check-app-user.txt"

          nape collect evidence \
          --control-activity "pet-medicine-host" \
          --file-path "pet-medicine-host/stdout-root-check-db-user.txt"

          nape collect evidence \
          --control-activity "pet-medicine-host" \
          --file-path "pet-medicine-host/stdout-user-exists-app-user.txt"

          nape collect evidence \
          --control-activity "pet-medicine-host" \
          --file-path "pet-medicine-host/stdout-user-exists-db-user.txt"

          nape collect evidence \
          --control-activity "rover-cloud" \
          --file-path "rover-cloud/cloud-config.yaml"

          nape collect evidence \
          --control-activity "exa-doo-dc" \
          --file-path "exa-doo-dc/soc1-report-analysis.json"
```
____

### Release 4

There is nothing to add for this release.  The demo uses Release 4 to simulate with drift looks like for such instances as an expired Exa-Doo SOC1 Report.

**RELEASE**
```text
4
```
