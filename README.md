cov-configure --config coverity_result/config/coverity-config.xml --gcc
cov-build.exe --config coverity_result/config/coverity-config.xml --dir coverity_result/idir make
cov-analyze.exe --dir coverity_result/idir/ --strip-path /c/Works/labs/tmp/c-example-project
