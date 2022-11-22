# bug report reproducing example

Minimal reproducing example for module import problem with null values.

# what is the problem?

Importing modules that export a null value
 - works for init, plan, apply
 - fails for destroy

 # reproduction

```
cd tf-module-two
terraform init # -> works
terraform plan # -> works
terraform apply # -> works
terraform destroy
# suddenly FAILS with
# Error: Unsupported attribute
# │ 
# │   on main.tf line 2, in locals:
# │    2:     imported_null_value = module.module_onenull_valued_output
# │     ├────────────────
# │     │ module.module_one is object with 1 attribute "string_valued_output"
# │ 
# │ This object does not have an attribute named "null_valued_output".
```

That is, the SAME CODE is valid for init, plan, apply, but invalid for destroy???

# tested versions

TODO test with various vanilla tf versions
