# AMI Resource

A Concourse resource for tracking AMI versions

## Source Configuration

* `access_key_id`: *Required.* The AWS access key to use.

* `secret_access_key`: *Required.* The AWS secret key to use.

* `region`: *Required.* the AWS region the AMIs are located in.

* `allow_no_matches`: *Optional.* Default `true`.  A boolean that specifies if the check should succeed in the case where no AMI is found that matches the search options.
  * `true` - Always succeed even if no matching AMI is found.
  * `false` - Fail if no matching AMI is found.

* `search_options`: Options to filter AMIs, see [supported options](http://docs.aws.amazon.com/sdkforruby/api/Aws/EC2/Client.html#describe_images-instance_method).

## Example:

```
- name: windows-ami
  type: ami
  source:
    access_key_id: key
    secret_access_key: secret
    region: us-east-1
    search_options:
      filters:
        - {name: "name", values: ["Windows_Server-2012-R2_RTM-English-64Bit-Base*"]}
        - {name: "state", values: ["available"]}
      owners:
        - amazon

```
