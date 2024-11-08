
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
