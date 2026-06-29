FROM gradle:7 AS base
CMD ["bash"]

# build
FROM base as test-and-build
COPY . /workspace
WORKDIR /workspace
RUN ./gradlew build

# production
FROM eclipse-temurin:17-jdk as production
COPY --from=test-and-build /workspace/build/libs/api-0.0.1-SNAPSHOT.jar ./api.jar
CMD [ "java", "-jar", "api.jar" ]

