### ASP.NET Core Runtime 2.1.3
FROM jonmcquade/dotnetcore-runtime-sdk-node-python:base
WORKDIR /
ARG dotNetVer="2.1.3"
ENV DOTNET_VERSION $dotNetVer
ENV ASPNETCORE_VERSION $dotNetVer
RUN apk add --no-cache \	
        ca-certificates \	
        \	
        # .NET Core dependencies	
        krb5-libs \	
        libcurl \	
        libgcc \	
        libintl \	
        libssl1.0 \	
        libstdc++ \	
        libunwind \	
        libuuid \	
        tzdata \	
        userspace-rcu \	
        zlib \	
    && apk -X https://dl-cdn.alpinelinux.org/alpine/edge/main add --no-cache \	
    	lttng-ust \	
		# .NET Core Runtime 	
	&& apk add --no-cache --virtual .build-deps \
        openssl \
    && wget -O dotnet.tar.gz https://dotnetcli.blob.core.windows.net/dotnet/Runtime/$DOTNET_VERSION/dotnet-runtime-$DOTNET_VERSION-linux-musl-x64.tar.gz \
    && dotnet_sha512='fb9a080141038545af3fced55acbd7ef0d4948d527115f67937bfb6eee012eff0c1e18858ccab43f2752711f2eda29445d2c42edf5557348686844b2046a3b54' \
    && echo "$dotnet_sha512  dotnet.tar.gz" | sha512sum -c - \
    && mkdir -p /usr/share/dotnet \
    && tar -C /usr/share/dotnet -xzf dotnet.tar.gz \
    && ln -s /usr/share/dotnet/dotnet /usr/bin/dotnet \
    && rm dotnet.tar.gz \
    && apk del .build-deps
