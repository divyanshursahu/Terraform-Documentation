### Locals in terraform

A local value assigns a name to an expression, so you can use the name multiple times within a module instead of repeating the expression.
A Local is only accessible within the local module vs a Terraform variable which can be scoped globally. Another thing to note is that a local in Terraform doesn’t change its value once assigned. A variable value can be manipulated via expressions. ]

references:

https://developer.hashicorp.com/terraform/language/values/locals
https://spacelift.io/blog/terraform-locals
