haproxy-github-https-expose
===========================

A simple haproxy config project to expose corporate github behind firewall to internet.


### Steps

- Install haproxy on Ubuntu

```
sudo apt-get -y install haproxy

haproxy -v

```

- Edit `/etc/haproxy/haproxy.cfg` with content in [haproxy.cfg](config/haproxy.cfg).

- Start haproxy

```
sudo service haproxy restart
```

- Look into ip address with `ifconfig`

- Expose to public internet with `ngrok`.

```
sudo snap install ngrok

ngrok http https://<ip-address from ifconfig>
```

- Get personal access token from corporate Github following [link](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token)

- Set https proxy for github

```
git config --global https.proxy  https://****.ngrok.io
```

- Git clone now works!!

```
git clone https://****.ngrok.io/<github-id/org>/<github-repo>
```

- Unset https proxy for github

```
git config --global --unset https.proxy
```