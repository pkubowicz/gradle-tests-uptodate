Demonstrates a failure of Gradle up-to-date checks, where renaming a non-related task can trigger tests re-execution:

1. Run `./gradlew barJar --console=verbose` - tests are run
2. Repeat `./gradlew barJar --console=verbose` - everything up-to-date
3. Edit `build.gradle`, changing `baz123` task name to `baz1234`
   - note that `barJar` is not related to this task in any way
4. Run `./gradlew barJar --console=verbose` - tests are re-run, although nothing related to `barJar` has changed

`--info` logs show only
```
Task ':test' is not up-to-date because:
  Task ':test' has additional actions that have changed
```
