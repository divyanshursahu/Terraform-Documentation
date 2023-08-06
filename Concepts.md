### Locals in terraform

A local value assigns a name to an expression, so you can use the name multiple times within a module instead of repeating the expression.
A Local is only accessible within the local module vs a Terraform variable which can be scoped globally. Another thing to note is that a local in Terraform doesn’t change its value once assigned. A variable value can be manipulated via expressions. ]

references:

https://developer.hashicorp.com/terraform/language/values/locals
https://spacelift.io/blog/terraform-locals


**Meta Arguments**
for_each
https://kodekloud.com/blog/terraform-for_each/#


**Modules**

So modules are basically containers that can be used to host multiple resources that can be used together.

The root modules contain the resources defined within your TerraForm configuration file in the main
