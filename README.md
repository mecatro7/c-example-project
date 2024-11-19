
## Coverity Classic

### Build Configuraiton
```sh
cov-configure --config coverity_result/config/coverity-config.xml --gcc
```

### Build 
```sh
cov-build --config coverity_result/config/coverity-config.xml --dir coverity_result/idir make
```

### Analysis
```sh
cov-analyze --dir coverity_result/idir/ --strip-path /c/Works/labs/tmp/c-example-project
```

### Commit
```sh
cov-commit-defects --dir coverity_result/idir/ --strip-path /c/Works/labs/tmp/c-example-project
```



## Coverty Scan
```sh
coverity scan --dir coverity_result/idir --local coverity_result/analysis
```


## Polaris Scan
### pass access token information using the BRIDGE_POLARIS_ACCESSTOKEN environment variable
export BRIDGE_POLARIS_ACCESSTOKEN=xxxxxxxx

### run synopsys-bridge using input file in json format

- inputFile.json
```json
{
        "data": {
                "polaris": {
                        "application": {
                                "name": "gwyi"
                        },
                        "project": {
                                "name": "c-example-project"
                        },
                        "branch": {
                "name": "main"
            },
                        "assessment": {
                                "types":  ["SAST"]
                        },
                        "serverUrl": "https://poc.polaris.synopsys.com"
                }
        }
}

```
```sh
synopsys-bridge --stage polaris --input inputFile.json
```


### run synopsys-bridge using parameters on the command line
```sh
synopsys-bridge --stage polaris \
polaris.application.name="gwyi" \
polaris.project.name="c-example-project" \
polaris.branch.name="main" \
polaris.assessment.mode="SOURCE_UPLOAD" \
polaris.assessment.types=SAST \
polaris.serverUrl=https://poc.polaris.blackduck.com
```


## Reference
- [Download Synopsys Bridge CLI](https://documentation.blackduck.com/bundle/bridge/page/documentation/c_download.html)
- [Passing Arguments using a JSON file](https://documentation.blackduck.com/bundle/bridge/page/documentation/c_run-commands-using-a-json-file.html)
- [Passing Arguments using the CLI](https://documentation.blackduck.com/bundle/bridge/page/documentation/c_run-commands-using-the-cli.html)
- [Passing build and clean commands to Coverity](https://documentation.blackduck.com/bundle/bridge/page/documentation/c_config_tools_using_bridge.html#c_config_tools_using_bridge__build_and_clean)
- [Managing your personal access tokens - github](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-fine-grained-personal-access-token)
