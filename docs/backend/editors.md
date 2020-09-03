# Editors

Our backend is written in Kotlin, a language developed by JetBrains... the same
people who develop IntelliJ IDEA. In other words, it is nearly mandatory to use
it for developing with Kotlin.

## Configuration

We're using [ktlint](https://github.com/pinterest/ktlint) to lint and format our
code, you shouldn't have to install it however as it's included as a
[Gradle](https://gradle.org/) plugin instead. To configure `ktlint` to format
code in IntelliJ and when you're comitting, run the following commands:

```sh
./gradlew ktlintApplyToIdea
./gradlew addKtlintCheckGitPreCommitHook
```

The latter command will make it so you cannot commit code that is improperly
formatted, so just be aware that if IntelliJ keeps failing to commit that is
probably the reason.
