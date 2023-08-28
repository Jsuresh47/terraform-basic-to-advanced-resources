## Day 17

🔖 This is Day 17 of learning Terraform (Infrastructure as a Code - IaaC).

So, let's get started! 🔰

### 🚀 SPLAT EXPRESSION

✔️ In Terraform, the splat expression is a powerful syntax used to access all the elements of a list, map, or set within a resource or data block.

*✅ Represented by the [*] symbol.*

✔️ The splat expression allows you to pass multiple elements from a data structure as separate arguments to a resource or data block.

🔖 For example,

Consider the following code,

where we have a list variable
"subnets" containing subnet IDs, and we want to create multiple AWS instances in each subnet using
Terraform's aws_instance resource:
```
variable "subnets" {
type = list(string)
default = ["subnet-1a", "subnet-1b", "subnet-1c"]
}
```
```
resource "aws_instance" "example" {
ami = "ami-0c55b159cbfafe1f0"
instance_type = "t2.micro"
subnet_id = var.subnets[*]
}
```
In this example,

we use the splat expression

*var.subnets[*]*

to pass all the subnet IDs as separate arguments to the

subnet_id attribute of the aws_instance resource.

As a result, Terraform will create an EC2 instance in each of the specified subnets.

✔️ The splat expression is an elegant feature in Terraform that enables efficient and concise handling of collections of resources or data.

✔️ It eliminates the need for writing repetitive code when dealing with multiple elements within a list, map, or set.

### 🚀 TERRAFORM GRAPH 📈

✔️ The terraform graph command is a useful tool to generate a visual representation of either a configuration or execution plan.

✔️ The output of the terraform graph is in the *DOT format*, which can be easily converted to an image using tools like Graphviz.

![Screenshot 2023-07-31 180954](https://github.com/sahdevgrover/terraform-basic-to-advanced-resources/assets/132704247/f674ddd7-2010-4a22-bf3d-148b27bd3d20)


### 🚀 SAVING TERRAFORM PLAN TO FILE

✔️ You can save the generated Terraform plan to a specific path using the -out flag with the terraform plan command.

✔️ This allows you to have a saved plan that can be used with terraform apply, ensuring that only the changes shown in the plan are applied.

🔖 For example:
```
✅ terraform plan -out=path
```
However, it's worth noting that this feature is not frequently used in production environments.

### 🚀 TERRAFORM OUTPUT

✔️ As you may have noticed in earlier classes, I have been showing the output of the configuration we created in our .tf file.

✔️ The terraform output command is used to extract the value of an output variable from the state file.

![Screenshot 2023-07-31 185457](https://github.com/sahdevgrover/terraform-basic-to-advanced-resources/assets/132704247/ca29a9ba-ed1e-4d0f-b55f-8eb72052abd1)

🔖 For instance,

if you have defined output variables like iam_names and iam_arns in your configuration file,

you can extract the output of iam_names only by running:
```
✅ terraform output iam_names
```
This way, you can selectively access specific output values.

![Screenshot 2023-07-31 185504](https://github.com/sahdevgrover/terraform-basic-to-advanced-resources/assets/132704247/30a34f55-b11c-4ea8-aa26-19da28631c9e)
