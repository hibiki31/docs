# Binardat 10G SW

2025年6月28日

寝室においても大丈夫くらいな音で発熱も大丈夫そう。いいMNGだった。

![IMG_3365](./binardat-10g-switch.assets/IMG_3365.JPG)

## 商品情報

[Binardat 8ポート10ギガビットマネージドスイッチ、4x10G RJ45イーサネット、1G/2.5G/5G/10G対応、4x10G SFP+、160Gbps帯域幅、L3ウェブマネージド、メタルネットワークスイッチ](https://www.amazon.co.jp/dp/B0DQ77BS64?ref=ppx_yo2ov_dt_b_fed_asin_title&th=1)

**4x10G Eth + 4x10G SFP Managed**でBGPも吐ける、￥31,999は良い。

![img](./binardat-10g-switch.assets/71UQZ0hAWgL._AC_SL1500_.jpg)

## 管理コンソールに接続

初期IPの`192.168.2.1`にアクセスする。`admin:admin`で入れる。

![image-20250628180539976](./binardat-10g-switch.assets/image-20250628180539976.png)

### ホーム

ポートのステータスが確認できる。MACやSerialは管理コンソールで消している。

![image-20250628180724785](./binardat-10g-switch.assets/image-20250628180724785.png)

### System Config

IP ConfigでVLANごとにIPをつけれる。

![image-20250628180905673](./binardat-10g-switch.assets/image-20250628180905673.png)

### Monitor Management

SSH ConfigでSSHの設定ができる。デフォルトは無効。

![image-20250628181144764](./binardat-10g-switch.assets/image-20250628181144764.png)

SSHしてみる。Ciscoライクやん。

```
ssh admin@192.168.2.1
Switch#
Switch#show running-config
!
no service password-encryption
!
hostname Switch
sysLocation Default
sysContact Default
!
multi config access
!
username admin privilege 15 password 0 admin
!
authentication line console login local
!
!
!

fanspeed auto
!
!
!
ssh-server enable
!
!
!
!
!
!
!
!
!
vlan 1
!
Interface Ethernet1/0/1
!
Interface Ethernet1/0/2
!
Interface Ethernet1/0/3
!
Interface Ethernet1/0/4
!
Interface Ethernet1/0/5
!
Interface Ethernet1/0/6
!
Interface Ethernet1/0/7
!
Interface Ethernet1/0/8
!
interface Vlan1
 ip address 192.168.2.1 255.255.255.0
!
no login
!
end

```

SNMP Config 吐けそうで良い。

![image-20250628181529624](./binardat-10g-switch.assets/image-20250628181529624.png)

### Switch Config

Jumbo Frame 9000にしたかったので良い。

![image-20250628181630880](./binardat-10g-switch.assets/image-20250628181630880.png)

### VLAN Config

VLAN ID 最大何個まで動くかは確認したい。

![image-20250628181726045](./binardat-10g-switch.assets/image-20250628181726045.png)

VLANハイブリットを初めて知った。Nativeはタグが付いていないフレームを受け取ったとき、UnTaggedは指定したVLANの時はタグを付けずに送る。複数指定するとヤバいと思うけどなぜ指定ができるのか。

![image-20250628190815472](./binardat-10g-switch.assets/image-20250628190815472.png)



### DHCP Config

DHCP Serverも搭載。

![image-20250628181829739](./binardat-10g-switch.assets/image-20250628181829739.png)

### ACL Config

L2, L3で書ける。時間帯の指定もできる。

![image-20250628181928023](./binardat-10g-switch.assets/image-20250628181928023.png)

### Ring Network

L2リング系のプロトコルも対応。Rapid STP対応しているのかな？

![image-20250628182014441](./binardat-10g-switch.assets/image-20250628182014441.png)

### Route Config

スタティックもダイナミックもそこそこ色々ある。

![image-20250628182135466](./binardat-10g-switch.assets/image-20250628182135466.png)

### Multicast Manage

IGMPあればとりあえず良い。

![image-20250628182226164](./binardat-10g-switch.assets/image-20250628182226164.png)

### QoS Config

まあ普通。

![image-20250628182307071](./binardat-10g-switch.assets/image-20250628182307071.png)

## SpeedTest

メインのデスクトップは2.5Gなのでほぼ理論値

![image-20250628191422077](./binardat-10g-switch.assets/image-20250628191422077.png)

## SNMP

- Global Config -> Agent State -> Enabled
- Community Config ->
  - Community Name -> public
  - Access Priority -> Readonly
