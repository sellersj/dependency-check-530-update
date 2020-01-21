# dependency-check-530-update

This is a minimal project to reproduce an issue when updating to owasp dependency check 5.3.0 when
using a very, very old tag lib. Specifically jakarta unstandard taglib.

## Maven command
```
mvn org.owasp:dependency-check-maven:5.3.0:check org.owasp:dependency-check-maven:5.3.0:aggregate -Dformat=ALL -DskipProvidedScope=true -DnuspecAnalyzerEnabled=false -DassemblyAnalyzerEnabled=false -DnodeAuditAnalyzerEnabled=false -DrubygemsAnalyzerEnabled=false -DbundleAuditAnalyzerEnabled=false
```

## Output
```
[INFO] Created CPE Index (1 seconds)
[WARNING] An error occurred while analyzing '/Users/sellersj/.m2/repository/taglibs/taglibs-unstandard/20060829/taglibs-unstandard-20060829.jar' (CPE Analyzer).
...
[ERROR] Failed to execute goal org.owasp:dependency-check-maven:5.3.0:check (default-cli) on project dependency-check-530-update: One or more exceptions occurred during dependency-check analysis: One or more exceptions occurred during analysis:
[ERROR] 	Unable to create a CPE for apache:standard_taglibs:-
[ERROR] -> [Help 1]
```

I have been able to reproduce this with maven 3.6.2 / 3.6.3, using java 8 on linux / mac.