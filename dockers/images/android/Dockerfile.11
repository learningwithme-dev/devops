# Use the OpenJDK 11 base image (needed for Android tools)
FROM openjdk:11-jdk



# Set environment variables
ENV ANDROID_HOME=/opt/android-sdk
ENV PATH=$ANDROID_HOME/cmdline-tools/latest/bin:$ANDROID_HOME/platform-tools:$ANDROID_HOME/build-tools:$PATH
ENV JAVA11_HOME=/usr/lib/jvm/java-11-openjdk-amd64

# Set default Java version to 11 for Android tools
ENV JAVA_HOME=$JAVA11_HOME
ENV PATH=$JAVA_HOME/bin:$PATH

# Install Android SDK Command-line Tools
RUN mkdir -p $ANDROID_HOME/cmdline-tools && \
    wget -q https://dl.google.com/android/repository/commandlinetools-linux-9477386_latest.zip -O cmdline-tools.zip && \
    unzip cmdline-tools.zip -d $ANDROID_HOME/cmdline-tools && \
    rm cmdline-tools.zip && \
    mv $ANDROID_HOME/cmdline-tools/cmdline-tools $ANDROID_HOME/cmdline-tools/latest

# Accept Android SDK licenses and install required components
RUN yes | $ANDROID_HOME/cmdline-tools/latest/bin/sdkmanager --licenses && \
    $ANDROID_HOME/cmdline-tools/latest/bin/sdkmanager --update && \
    $ANDROID_HOME/cmdline-tools/latest/bin/sdkmanager \
        "platform-tools" \
        "platforms;android-33" \
        "build-tools;33.0.2"

# Install Gradle
RUN wget -q https://services.gradle.org/distributions/gradle-7.6-bin.zip -O gradle.zip && \
    unzip gradle.zip -d /opt && \
    rm gradle.zip && \
    ln -s /opt/gradle-7.6/bin/gradle /usr/bin/gradle

# Verify installations
RUN java -version && gradle -v && $ANDROID_HOME/cmdline-tools/latest/bin/sdkmanager --list

# Set working directory
WORKDIR /workspace

# Default command
CMD ["bash"]