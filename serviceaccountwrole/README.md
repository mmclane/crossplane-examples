# Service account IAM policy

This package should create an IAM role and policy that can be assumed by a k8s service account to provide pods access to AWS resources.  


Reference: 
* https://github.com/upbound/provider-terraform 
* https://marketplace.upbound.io/providers/upbound/provider-terraform/v0.5.0/resources/tf.upbound.io/Workspace/v1beta1
* https://github.com/terraform-aws-modules/terraform-aws-iam/tree/v5.30.0/modules/iam-eks-role 

## Example:

```
apiVersion: iam.doc.network/v1alpha1
kind: ServiceAccountwRole
metadata:
  name: m3test
  namespace: default
spec:
  clusterName: dev
  env: dev
  project: m3test
  description: This is a test
  policy: |
      {
          "Version" : "2012-10-17",
          "Statement" : [
              {
                  "Effect" : "Allow",
                  "NotAction" : "iam:*",
                  "Resource" : "*"
              }
          ]
      }
```
