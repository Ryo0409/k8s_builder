# k8s_builder
- kubernetesをEC2ベースで作成するためのツール

### 手順
#### ① Cloudformationを用いてControl plane及びWorker nodeを作成する
- `create_ec2_for_k8s.yaml`を使用。
  - stack名、アクセス用ユーザの認証情報、Worker nodeの数を指定。

#### ② Control plane用のnodeにアクセスする

#### ③ Control plane用のnodeでplaybookを実行する
- 以下コマンドを実行する。
```
git clone https://github.com/Ryo0409/k8s_builder.git
cd k8s_builder/ansible/
ansible-playbook -i inventory/aws_ec2.yml playbooks/install_k8s.yaml -e target=all -u <ユーザ名> -kK
```
