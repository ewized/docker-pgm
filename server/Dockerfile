FROM isuper/java-oracle

RUN apt update && apt install -y \
    git \
    maven \
    rake \
  && apt clean

WORKDIR /tmp

ARG SPORTBUKKIT_URL="https://github.com/OvercastNetwork/SportBukkit.git"
ARG GIT_EMAIL="ewized@ewized.com"
ARG GIT_USER="ewized"

RUN git config --global user.email "$GIT_EMAIL" && git config --global user.name "$GIT_NAME"
RUN mkdir -p /root/.m2/ && echo "<settings><profiles><profile><id>projectares</id><repositories><repository><id>freundtech</id><url>https://repo.freundTech.com</url></repository></repositories></profile></profiles><activeProfiles><activeProfile>projectares</activeProfile></activeProfiles></settings>" > /root/.m2/settings.xml

RUN git clone "$SPORTBUKKIT_URL" && cd SportBukkit && rake
RUN mv /tmp/SportBukkit/build/CraftBukkit/target/sportbukkit*.jar /root/sportbukkit.jar && rm -Rf /tmp

WORKDIR /root

VOLUME ["/root"]

EXPOSE 25565

CMD ["java", "-Xmx1G", "-jar", "sportbukkit.jar"]
