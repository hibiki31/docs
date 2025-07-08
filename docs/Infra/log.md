# Log

## openobserve

## Fluent Bit

[公式（Ubuntu）](https://docs.fluentbit.io/manual/installation/linux/ubuntu)

```bash
curl https://raw.githubusercontent.com/fluent/fluent-bit/master/install.sh | sh
```

### 最小構成

`/etc/fluent-bit/fluent-bit.conf`

```conf
[SERVICE]
    Flush        5
    Daemon       Off

[INPUT]
    Name              systemd
    Tag               host.*
    Read_From_Tail    On
    DB                /var/log/flb_systemd.db

[OUTPUT]
  Name http
  Match *
  URI /api/default/default/_json
  Host xxxx
  Port 5080
  tls Off
  Format json
  Json_date_key    _timestamp
  Json_date_format iso8601
  HTTP_User XXXX
  HTTP_Passwd XXXX
  compress gzip
```

```bash
sudo usermod -aG systemd-journal fluent-bit
sudo systemctl restart fluent-bit
```

デバッグ

```bash
/opt/fluent-bit/bin/fluent-bit -c /etc/fluent-bit/fluent-bit.conf
```
