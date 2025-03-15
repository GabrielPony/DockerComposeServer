# 使用 Ubuntu 22.04 作为基础镜像
FROM ubuntu:22.04

# 设置环境变量，避免交互式提示
ENV DEBIAN_FRONTEND=noninteractive

# 声明变量
ARG USERNAME=gabriel
ARG PASSWORD=1111

# 备份原有源列表
RUN cp /etc/apt/sources.list /etc/apt/sources.list.bak

# 替换源为阿里云源
RUN sed -i 's|http://archive.ubuntu.com/ubuntu/|http://mirrors.aliyun.com/ubuntu/|g' /etc/apt/sources.list && \
    sed -i 's|http://security.ubuntu.com/ubuntu/|http://mirrors.aliyun.com/ubuntu/|g' /etc/apt/sources.list

# 安装必要的工具
RUN apt-get update && apt-get install -y \
    sudo \
    curl \
    vim

# 创建一个新用户
RUN useradd -m -s /bin/bash ${USERNAME} && \
    echo "${USERNAME}:${PASSWORD}" | chpasswd && \
    usermod -aG sudo ${USERNAME}

# 切换到新用户
USER ${USERNAME}

# 设置工作目录
WORKDIR /home/${USERNAME}

# 设置默认命令
CMD ["/bin/bash"]
