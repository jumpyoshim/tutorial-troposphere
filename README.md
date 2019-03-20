# tutorial-troposphere

## Set Up Locally

```sh
$ docker-compose up
```

## Example

```sh
$ docker-compose exec app bash
root@11fe9706d256:/app# ipython
In [1]: from troposphere import Ref, Template

In [2]: import troposphere.ec2 as ec2

In [3]: t = Template()

In [4]: instance = ec2.Instance("myinstance")

In [5]: instance.ImageId = "ami-951945d0"

In [6]: instance.InstanceType = "t1.micro"

In [7]: t.add_resource(instance)
Out[7]: <troposphere.ec2.Instance at 0x7f792f773860>

In [8]: print(t.to_json())
{
    "Resources": {
        "myinstanc": {
            "Type": "AWS::EC2::Instance"
        },
        "myinstance": {
            "Properties": {
                "ImageId": "ami-951945d0",
                "InstanceType": "t1.micro"
            },
            "Type": "AWS::EC2::Instance"
        }
    }
}
In [9]: print(t.to_yaml())
Resources:
  myinstanc:
    Type: AWS::EC2::Instance
  myinstance:
    Properties:
      ImageId: ami-951945d0
      InstanceType: t1.micro
    Type: AWS::EC2::Instance
```
