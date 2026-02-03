# Rover Medical System
The Rover Medical demo for how an Assured Release happens in thin slices over time.



## Release 1

Ensure that after the ```nape start collect ...``` command, the below ```nape collect evidence ...``` is the only command that exists in the [systems-cicd.yml](.github/workflows/system-cdicd.yml):

```bash
          echo "--- Release 1 - Evidence Collection --- "

          nape collect evidence \
            --control-activity "pet-medicine-app" \
            --file-path "pet-medicine-app/app-config.toml"
```

## Release 2

Add the below ``nape collect evidence ...``` command after the Release 1 command

```bash
          echo "--- Release 2 - Evidence Collection (Additions) --- "

          nape collect evidence \
            --control-activity "pet-medicine-db" \
            --file-path "pet-medicine-db/my-db.ini"

```

## Release 3

Add the below ``nape collect evidence ...``` commands after the Release 2 command

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


## Release 4

There is nothing to add for this release.  The demo uses Release 4 to simulate with drift looks like for such instances as an expired Exa-Doo SOC1 Report.