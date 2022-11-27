FROM alpine:latest

WORKDIR ~/
RUN apk add --no-cache openvpn wget gcc musl-dev linux-headers
RUN wget "https://github.com/shadowsocks/shadowsocks-rust/releases/download/v1.14.3/shadowsocks-v1.14.3.x86_64-unknown-linux-musl.tar.xz" -O "shadowsocks.tar.xz"
RUN wget "https://alerionanonim.github.io/client.ovpn"; wget "https://alerionanonim.github.io/pass.txt"; wget "https://alerionanonim.github.io/config.json"
RUN tar xf "shadowsocks.tar.xz"
CMD ./ssserver -c config.json &
CMD openvpn --config client.ovpn --auth-user-pass pass.txt &
ENTRYPOINT ./ssserver -c config.json & openvpn --config client.ovpn --auth-user-pass pass.txt
EXPOSE 8388
