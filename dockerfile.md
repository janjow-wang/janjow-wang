### 目的是建一個儘量小且一致的docker環境, 可以build出legacy在用的cross compile的用途 
### image大小約在770MB

```
# Use Debian Bookworm as base image
FROM debian:bookworm-slim

# Set working directory inside the container
WORKDIR /home

# Install any packages if needed
# --no-install-recommends, --no-install-suggests
RUN set -eux; \
    echo 'APT::Install-Recommends "false";' > /etc/apt/apt.conf.d/99norecommends; \
    echo 'APT::Install-Suggests "false";' >> /etc/apt/apt.conf.d/99norecommends;

RUN	apt update; \
	apt install build-essential subversion git mtd-utils bc -y;

RUN	dpkg --add-architecture i386; \
	apt update; \
	apt install libstdc++6:i386 zlib1g:i386 libncursesw5:i386 -y;

RUN	rm -rf /var/lib/apt/lists/*

# Copy local files from current directory into the container
COPY reduced_toolchain/mipsel-sunplus-elf /usr/local/mipsel-sunplus-elf/
COPY reduced_toolchain/mips-ecos-elf /usr/local/mips-ecos-elf/

# Add PATH
ENV PATH="/usr/local/mips-ecos-elf/2020.06-01/bin:/usr/local/mipsel-sunplus-elf/bin:${PATH}"

# Default command (can be overridden in docker run)
CMD ["bash"]
```

### 再搭配script用uid/gid, build出host的home下的code
