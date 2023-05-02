### Enabling Debug Mode

There could be a bug or malformed input within your workflow, which may result in your resources not provisioning as intended. In such rare cases, it’s important to know how to access detailed logs describing what Terraform is doing. They may aid in pinpointing the cause of the error, tell you if it’s user-made, or prompt you to report the issue to Terraform developers if it’s an internal bug.

Terraform exposes the TF_LOG environment variable for setting the level of logging verbosity. There are five levels:

**TRACE:** the most elaborate verbosity, as it shows every step taken by Terraform and produces enormous outputs with internal logs.

**DEBUG:** describes what happens internally in a more concise way compared to TRACE.

**ERROR:** shows errors that prevent Terraform from continuing.

**WARN:** logs warnings, which may indicate misconfiguration or mistakes, but are not critical to execution.

**INFO:** shows general, high-level messages about the execution process.


To specify a desired log level, you’ll have to set the environment variable to the appropriate value:

``` export TF_LOG=log_level ```
