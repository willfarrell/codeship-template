FROM willfarrell/codeship-base AS base

FROM gradle:5.2-jdk-alpine

ARG workdir=/data
ARG bin=/usr/local/bin/codeship

#ENV PATH="${PATH}:${bin}"

RUN apk update && \
    apk add --no-cache bash openssl git openssh-client




USER root
# https://developer.android.com/studio/
ARG ANDROID_SDK_BUILD=4333796
ARG SDK_URL="https://dl.google.com/android/repository/sdk-tools-linux-${ANDROID_SDK_BUILD}.zip"

ARG ANDROID_HOME="/usr/local/android-sdk"
# https://en.wikipedia.org/wiki/Android_version_history
ARG ANDROID_VERSION=28
# https://developer.android.com/studio/releases/build-tools
ARG ANDROID_BUILD_TOOLS_VERSION=28.0.3
ARG ANDROID_LICENSE="24333f8a63b6825ea9c5514f83c2829b004d1fee"

ENV PATH="${PATH}:${bin}:${ANDROID_HOME}/tools/bin"

# Download Android SDK
RUN mkdir "$ANDROID_HOME" .android && \
    cd "$ANDROID_HOME" && \
    curl -o sdk.zip ${SDK_URL} && \
    unzip sdk.zip && \
    rm sdk.zip && \
    mkdir "${ANDROID_HOME}/licenses" || true && \
    echo "${ANDROID_LICENSE}" > "${ANDROID_HOME}/licenses/android-sdk-license"

# Install Android Build Tool and Libraries
RUN sdkmanager --update && \
    sdkmanager "build-tools;${ANDROID_BUILD_TOOLS_VERSION}" \
       "platforms;android-${ANDROID_VERSION}" \
       "platform-tools" && \
    yes | sdkmanager --licenses

# Install Build Essentials
RUN apk add --no-cache build-base

COPY --from=base ${bin}/ ${bin}/
WORKDIR ${workdir}
