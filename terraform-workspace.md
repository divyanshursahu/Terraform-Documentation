# Terraform Workspace

Now, why did TerraForm actually come up with this concept of having workspaces in place?

This is primarily used when you have your infrastructure deployed on multiple environments.

So normally companies definitely would have different environments.

So for example, they might have one environment for development, one for staging and another for production.

When a developer develops an application, they would first deploy their application on the development

infrastructure, which would be separate.

Then it had to be tested by users.

It might be taken from a development environment and put in the stealing infrastructure.

And finally, when needs to move on to production, it would move on to the production infrastructure.

Normally, mostly the configuration of each environment would be the same.

You might probably just have the production infrastructure having a higher hardware configuration.

So in this case, you have to work with similar infrastructure for each environment.

We built TerraForm configuration files.

Correct.

To build our infrastructure.

So an example, just looking here, let's say that we had infrastructure on ACL, we had a test network

and we had a staging network.

They both have the similar sort of resources.

The core difference here is the Test Network has an address space.

The stating network has a different address space.

The subnet e has an address space depending upon the space of the test network and the subnet has an

error space depending upon the address space of the staging network.

So both of these environments are different.

You might have the application being hosted here first for testing purposes and then it could move on

to the staging environment where it could be tested by users.

Similar environments, similar infrastructure, but different environments.

Now you could have multiple copies of your TerraForm configuration files, one for your Test network

and the other for the staging environment.

But again, you don't want to manage multiple copies and you could be having multiple environments.

Instead, you might just want to have, let's say, one set of TerraForm configuration files.

But then you want the values of certain resources to basically change depending upon the environment

it is being used for.

When it comes on to reform, one important concept that we've learned is the state of the resources.

The state of your resources in one environment could be different.

The state of resources in another environment can be different.

And again, what do I mean by this?

Let's say that your application is first being tested in your test environment before it moves on to

the staging environment where it is tested by end users by our UAT group of users.

In such a case.

You do want to provision this infrastructure right now because if you do that and it's not being used,

you are bearing a cost.

Let's say it takes a week to test out the changes of the application deployed in your test environment.

You don't want your staging infrastructure to be up and running for a week, but ideal in nature where

you have no application tested.

It's once this environment is complete, it's no longer required.

Testing is completed.

Then you provision the environment, move the application here, and probably destroy this environment.

So the state is very important.

If you have only one state right, it could be difficult to manage the state in four different environments

at a time, especially when you have similar infrastructure and you want one environment to be up and

running and the other to not run at this point in time, but at a later point in time.

Yes.

You could find ways and means to kind of manage this within your TerraForm configuration, but then

it will start getting complex in nature.

You want to manage probably one state separately for your test environment and one state separately

for your staging environment.

That is where you can actually make use of the workspaces concept in TerraForm.

You could have your same TerraForm configuration files in place, but you can have one workspace defined

specifically for, let's say, your test environment.

That would have its own state and another workspace for the staging environment that would have its

own state.

It's as simple as that.

That's one of the key reasons why you would want to make use of workspaces.

So in this chapter, folks want to give an introduction on TerraForm Workspaces.

Let's move on to the subsequent chapters to see how we can work with TerraForm Workspaces.
