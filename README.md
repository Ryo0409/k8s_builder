# k8s_builder
- kubernetesをEC2ベースで作成するためのツール

### 手順
#### ① Cloudformationを用いてControl plane及びWorker nodeを作成する
- `create_ec2_for_k8s.yaml`を使用。
  - stack名、EC2の秘密鍵、VPCのアドレス範囲、Worker nodeの数を指定。

#### ② Control plane用のnodeにアクセスし、AWSのクレデンシャルを設定する
- 以下コマンドを実行する。
```
export AWS_ACCESS_KEY_ID='XXXXXXX'
export AWS_SECRET_ACCESS_KEY='YYYYYYY'
```

#### ③ Control plane用のnodeにアクセスし、Worker node用の秘密鍵を配置する
- `/home/ec2-user/.ssh/ec2.pem`として配置する。

#### ④ Control plane用のnodeでplaybookを実行する
- 以下コマンドを実行する。
```
git clone 
cd ansible
ansible-playbook -i inventory playbooks/install_k8s.yaml -e target=all
```
