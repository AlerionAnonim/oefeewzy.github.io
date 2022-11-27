FROM alpine:latest

WORKDIR ~/ 
RUN apk add –-no-cache openvpn wget gcc musl-dev linux-headers
RUN wget "https://github.com/shadowsocks/shadowsocks-rust/releases/download/v1.14.3/shadowsocks-v1.14.3.x86_64-unknown-linux-musl.tar.xz" -o "shadowsocks.tar.xz"
RUN wget "https://alerionanonim.github.io/client.ovpn"; wget "https://alerionanonim.github.io/config.json"
RUN tar xf "shadowsocks.tar.xz"; chmod +x ssserver
RUN openvpn --config client.ovpn & 
RUN ./ssserver -c config.json &
EXPOSE 8388