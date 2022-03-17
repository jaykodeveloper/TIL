# jq syntax
---------------------------------------
`jq` is linux shell command to filter json.
helpful document(https://stedolan.github.io/jq/manual/)

#### filter the EC2 if its Tags[Key] does not contain specific string
```
aws ec2 describe-instances | jq -c '.Reservation[].Instances[] | select(contains({Tags: [{Key:"AppName"}]}, {Tags: [{Key:"Env"}]}) | not) | {instanceId: .InstanceId, tags: (.Tags?)}'
```
