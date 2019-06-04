FROM ubuntu
RUN apt-get update -y
ENV DEBIAN_FRONTEND=noninteractive
EXPOSE 80 443 2222
RUN apt-get install ca-certificates curl openssh-server tzdata git vim -y
WORKDIR /tmp
RUN curl -LO https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh
RUN bash /tmp/script.deb.sh
RUN apt-get install gitlab-ce
RUN touch script.sh
RUN echo "Port 2222" >> /etc/ssh/sshd_config
RUN echo "gitlab_rails['gitlab_shell_ssh_port'] = 2222" >> /etc/gitlab/gitlab.rb
RUN echo "nginx['redirect_http_to_https'] = true" >> /etc/gitlab/gitlab.rb
RUN echo "nginx['redirect_http_to_https_port'] = 80" >> /etc/gitlab/gitlab.rb
RUN echo "letsencrypt['enable'] = true" >> /etc/gitlab/gitlab.rb
RUN echo "/opt/gitlab/embedded/bin/runsvdir-start &" >> script.sh
RUN echo "sed -i 's/http\:\/\//https\:\/\//g' /etc/gitlab/gitlab.rb" >> script.sh
RUN echo "sed -i 's/gitlab.example.com/192.168.99.100/g' /etc/gitlab/gitlab.rb" >> script.sh
RUN echo "gitlab-ctl reconfigure" >> script.sh
RUN echo "service ssh restart" >> script.sh
RUN echo "tail -f /dev/null" >> script.sh
CMD ["sh","script.sh"]
