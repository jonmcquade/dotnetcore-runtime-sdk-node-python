### ASP.NET Core Runtime 2.1.0-preview1-26216-03
FROM jonmcquade/dotnetcore-runtime-sdk-node-python:base
WORKDIR /
ARG dotNetVer="2.1.0-preview1-26216-03"	
ENV DOTNET_VERSION $dotNetVer
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
    && wget -O dotnet.tar.gz https://dotnetcli.blob.core.windows.net/dotnet/Runtime/$DOTNET_VERSION/dotnet-runtime-$DOTNET_VERSION-alpine.3.6-x64.tar.gz \	
    && dotnet_sha512='2462480ccfb69308d61749122814de7b398e21eee952e597c7812c529a41394dad7411d6654f984f30f0e1c5e0ef8ce4749e247e12cc66bc49b69a1951d803f6' \	
    && echo "$dotnet_sha512  dotnet.tar.gz" | sha512sum -c - \	
    && mkdir -p /usr/share/dotnet \	
    && tar -C /usr/share/dotnet -xzf dotnet.tar.gz \	
    && ln -s /usr/share/dotnet/dotnet /usr/bin/dotnet \	
    && rm dotnet.tar.gz \	
    && apk del .build-deps