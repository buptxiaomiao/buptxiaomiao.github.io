# sqoop
DOC: https://sqoop.apache.org/docs/1.4.7/SqoopUserGuide.html

## sqoop import 采用字符串split-by  
  refer: https://community.cloudera.com/t5/Support-Questions/Sqoop-split-by-on-a-string-varchar-column/td-p/165528

```
sqoop job -Dorg.apache.sqoop.splitter.allow_text_splitter=true \\
    --create ${JOB_NAME} \\
    -- \\
    import \\
    --connect \"${JDBC}\" \\
    --username ${SOURCE_USR} \\
    --password-file ${PWD_FILE_PATH} \\
```

