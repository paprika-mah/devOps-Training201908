前提: 環境はオレゴン

Prepare0.yamlを実行する 事前に鍵を作成しておいてマネジメントコンソールから実行。


※タスク3の10は何故か、テキストのコピペで失敗。qwikLabのコピペで実行できた(簡単にみたかんじ差はなさそう),
念の為、下記に引用したので、こっち使うこと

opsOutput=$(aws opsworks-cm create-server --engine "Chef" --engine-model "Single" \
--engine-version "12" --server-name "MyAutomateServer" \
--instance-profile-arn $Ec2InstanceProfileArn \
--instance-type "m4.large" --key-pair $KeyName \
--service-role-arn $OpsWorksCmServiceIAMRole \
--security-group-ids $ChefServerSecurityGroup \
--subnet-ids $ChefServerSubnetId --region $Region \
--query 'Server.[Endpoint, EngineAttributes[*].Value]' --output text)


↑原因解決。
Bookshelfのドキュメントは改行が読み込めずおかしい模様。　要注意！！

基本的にドキュメントベースで進めてくれれば完成します！