1. Configure `gradle.properties` file:
    - Set appropriate values for artifactoryUrl, artifactoryUser, and artifactoryPassword
    - Change GAV 'group' property from `com.jfrog.bug` to something else (optional)
2. Build the "shadow" JAR (GAV classifier: standalone), also known as a "fat" or "uber" JAR:
    - Linux: `./gradlew shadowJar`   (verify that the `gradlew` script has +X permissions)
    - Windows: `gradlew.bat shadowJar`
3. Publish the artifacts
    - Linux: `./gradlew publish`
    - Windows: `gradlew.bat publish`
4. Locate published artifacts in Artifactory at GAV: com.jfrog.bug:shadow-gav:0.1-SNAPSHOT
5. Wait for Xray to finish scanning these artifacts
6. Select the *-standalone.jar artifact in Artifactory's tree browser, navigate to the 'Xray' tab
7. Click "More Details in Xray"
8. Notice you are taken to a different GAV in Xray.
    - In my instance, it seems to consistently pick 'io.dropwizard:dropwizard-assets'
9. Search for 'shadow-gav' in the Xray components screen
10. Xray finds the POM and -sources and -javadoc artifacts, but not the plain JAR nor the -standalone JAR.
