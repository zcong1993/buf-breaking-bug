# buf demo

Here is a demo to reproduce the bug.

1. build base image in master branch: `buf build -o base.bin`
2. build feature image in feat branch: `git checkout feat && buf build -o feat.bin`
3. detect breaking change using buf: `buf breaking -v --against base.bin feat.bin`

Then we got error:

```bash
b.proto:1:1:Previously present message "ARequest" was deleted from file.
```

but it works fine when using `buf breaking -v --against ".git#branch=master"` in feat branch.
