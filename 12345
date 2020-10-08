mkdir /tmp/Naive/
cd /tmp/Naive
nano /etc/sysctl.conf
wget -P /usr/local/bin "https://daofa.cyou/c1/caddy.tar"
tar -xvf /usr/local/bin/caddy.tar -C /usr/local/bin
rm /usr/local/bin/caddy.tar
whereis caddy
chown root:root /usr/local/bin/caddy
chmod 755 /usr/local/bin/caddy
setcap 'cap_net_bind_service=+ep' /usr/local/bin/caddy
cat /etc/group | grep www-data
cat /etc/passwd | grep www-data
groupadd -g 33 www-data
useradd -g www-data --no-user-group --home-dir /var/www --no-create-home --shell /usr/sbin/nologin --system --uid 33 www-data
mkdir /etc/caddy
mkdir /etc/ssl/caddy
chown -R root:root /etc/caddy
chown -R root:www-data /etc/ssl/caddy
chmod 770 /etc/ssl/caddy
touch /var/log/caddy.log
chown root:www-data /var/log/caddy.log
chmod 770 /var/log/caddy.log
mkdir -p /var/www/html
chown -R www-data:www-data /var/www
touch /etc/systemd/system/caddy.service
chown root:root /etc/systemd/system/caddy.service
chmod 644 /etc/systemd/system/caddy.service
systemctl daemon-reload
head /dev/urandom | tr -dc a-z0-9 | head -c 16 ; echo ''
chown root:root /etc/caddy/Caddyfile
chmod 644 /etc/caddy/Caddyfile
systemctl start caddy
systemctl status caddy
systemctl enable caddy


apt install libnss3 -y
wget https://github.com/klzgrad/naiveproxy/releases/download/v85.0.4183.83-4/naiveproxy-v85.0.4183.83-4-linux-arm64.tar.xz
apt install xz-utils
tar -xf naiveproxy-v85.0.4183.83-4-linux-arm64.tar.xz
cd naiveproxy-v85.0.4183.83-4-linux-arm64
cp naive /usr/local/bin
touch /etc/systemd/system/naive.service
echo [Unit] >/etc/systemd/system/naive.service
echo Description=NaiveProxy Server Service >>/etc/systemd/system/naive.service
echo After=network-online.target >>/etc/systemd/system/naive.service
echo [Service] >>/etc/systemd/system/naive.service
echo Type=simple >>/etc/systemd/system/naive.service
echo User=nobody >>/etc/systemd/system/naive.service
echo CapabilityBoundingSet=CAP_NET_BIND_SERVICE >>/etc/systemd/system/naive.service
echo ExecStart=/usr/local/bin/naive /etc/naive/config.json >>/etc/systemd/system/naive.service
echo [Install] >>/etc/systemd/system/naive.service
echo WantedBy=multi-user.target >>/etc/systemd/system/naive.service
cd ..
systemctl daemon-reload
mkdir /etc/naive
touch /etc/naive/config.json
echo { >/etc/naive/config.json
echo "listen": "http://127.0.0.1:8080", >>/etc/naive/config.json
echo "padding": true >>/etc/naive/config.json
echo } >>/etc/naive/config.json


systemctl enable naive
systemctl start naive
systemctl status naive
ufw allow 22
ufw allow 2222
ufw allow 80
ufw allow 443
