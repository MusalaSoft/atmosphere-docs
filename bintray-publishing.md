# Publishing to Bintray

## Publishing to Bintray with gradle task
This page contains information about how to publish a new release of specific Atmosphere project to the Bintray repo.

Open a console/terminal and navigate to the project root folder and run the following command:
* for Linux/macOS:
```
./gradlew bintrayUpload
    -Dbintray.user=<BINTRAY_USERNAME> \
    -Dbintray.key=<BINTRAY_API_KEY> \
    -Dgpg.pass=<ATMOSPHERE_PASSPHRASE> \
```
* for Windows:
```
gradlew bintrayUpload
    -Dbintray.user=<BINTRAY_USERNAME> ^
    -Dbintray.key=<BINTRAY_API_KEY> ^
    -Dgpg.pass=<ATMOSPHERE_PASSPHRASE> ^
```
For the credentials you should contact the administrator of the repo.

## Manually publishing to Bintray
The manual publishing is heavy and boring process. We do not recommend doing it unless you have a good reason (for example if the gradle task not working).
- Create `<project_name>-<vesion>.pom` file. Make sure that you have included all the dependencies. The `*.pom` file should look like this:
```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.musala.atmosphere</groupId>
  <artifactId>atmosphere-commons</artifactId>
  <version>0.1.1</version>
  <dependencies>
    <dependency>
      <groupId>log4j</groupId>
      <artifactId>log4j</artifactId>
      <version>1.2.17</version>
      <scope>runtime</scope>
    </dependency>
    <dependency>
      <groupId>commons-cli</groupId>
      <artifactId>commons-cli</artifactId>
      <version>1.2</version>
      <scope>runtime</scope>
    </dependency>
    <dependency>
      <groupId>org.apache.commons</groupId>
      <artifactId>commons-lang3</artifactId>
      <version>3.3.2</version>
      <scope>runtime</scope>
    </dependency>
    <dependency>
      <groupId>com.musala.atmosphere</groupId>
      <artifactId>framework-api19</artifactId>
      <version>0.0.1</version>
      <scope>runtime</scope>
    </dependency>
    <dependency>
      <groupId>com.google.code.gson</groupId>
      <artifactId>gson</artifactId>
      <version>2.8.0</version>
      <scope>runtime</scope>
    </dependency>
  </dependencies>
</project>
```
For reference you can see the `pom` file for a project in the Atmosphere Bintray repo.

- Open `build.gradle` file and change the `version`.

- Build the project with `gradlew build` command.

- Run `gradlew sourcesJar` and `gradlew javadocJar` to generate the `<project_name>-<version>-javadoc.jar` and `<project_name>-<version>-sources.jar` files.

- Sign the `jar` files with `gpg`.
    - Import the private key: `gpg --import private.key`
    - Import public key `gpg --import public.key`
    - Sign the `jar` files and the `pom` file with `gpg --sign -ab <file>`. The command should generate `*.asc` file.

    > To make a signature you should have GnuPG installed.

- Upload the `jar` files, `pom` and the `asc` files to the Bintray repo. [Here](https://jfrog.com/knowledge-base/how-do-i-upload-my-stuff-to-bintray/) is the official guide that explains how to upload files to Bintray.

## Verifying a signature
* download the public key of MusalaSoft organization from Bintray from [here](https://bintray.com/user/downloadSubjectPublicKey?username=musala).
* add the `musala-public.key.asc` to your public key ring with `gpg --import musala-public.key.asc`. To list the keys in your public key ring use `gpg --list-keys`.
* verify the signature with `gpg --vetify <FILE_SIGNATURE> <FILE>`. You should see something like this:
```
gpg: Signature made Tue, Jun 12, 2018  2:14:21 PM FLEDT using RSA key ID 703C021A
gpg: Good signature from "Atmosphere Framework <atmosphere@musala.com>"
...
```
>To verify the signature you should have GnuPG installed.
