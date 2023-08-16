# Security

Nothing is inherently secure in IT. However, things can be made harder to attack.

These set of rules help making an attack harder.

## Generalities

### TODO_CODE - Consider Everything Already Hacked

Always consider that the application you are writing, the container you are building or the node you are setting up is already hacked.

What information do the attacker has access to ? Credentials ? Encrypt them. Open port ? Close them. Root access ? Run as a user. Writing permissions ? Differentiate owner and executor of source files.

By considering everything already hacked, you can clearly see what needs additional security measures. Fix them.

### TODO_CODE - Use Minimal Permissions

You should always give minimal permissions wether in the production environment or the CI/CD tooling and organization member accesses. However, make sure that factorization is always considered **before** this step. Avoid duplication, and if a reorganization is required, reorganize.

A drawback of this rule is that access and management of the production environment and the CI/CD tools can become unbelievably hard is done badly.
This can be overcome by using standards, containers or tools to avoid manual management by all cost.

### TODO_CODE - Keep Your Software Up To Date

There is a tremendous amount of new vulnerabilities found every day. Those vulnerabilities are often patched rapidly so you should alway keep your software up to date to make sure those vulnerabilities include those patches.

## Executables

### TODO_CODE - Strip Executables

Use the `strip --strip-all` command to remove all the documentation symbols and reduce the executable size.

### TODO_CODE - Use Obfuscation

Obfuscate your code when possible using specialized tool for your language.

### TODO_CODE - Remove Symbol Addresses

When using `readelf` or `nm`, a user should not be able to see the address of the symbols within an executable.

This avoids attacks based on symbols address offset.

## Containers

Containers are a great part of today's IT environment. Making sure they are secured if very important.

`nonroot` distroless containers with statically linked compiled stripped executables are great for production environment, whereas CI containers can be less secure but from known internal sources.

### TODO_CODE - Avoid Using `root` User

For production containers, you should always run as a non-root user.

Specify the `USER` instruction in the `Dockerfile` and make sure the files have minimal permissions required by this user.

### TODO_CODE - Make Executables Read-Only

Make sure the executables files have only `r-x` permissions to the user executing the code.

The executables can either be owned by a specific user or by `root`, a specific user being preferred.

### TODO_CODE - Use Minimal Dependencies

Never include unused dependencies within a container. More dependencies means more potential vulnerabilities.

### TODO_CODE - Use An Entrypoint With Default Command

Always specify an `ENTRYPOINT` in the `Dockerfile` with a default `CMD`.

This is done to avoid an attacker

### TODO_CODE - Consider Every Layer Is Into The Final Image

Every layer of a container image is stored and cached.

This means that if secrets or files are copied into the image and then removed, they remain in the layer.

Hence, anyone can access it even if it is not in the final image. Never add sensitive files or source code within the final container.

To avoid this issue, use _multiple step image building_.

### TODO_CODE - Use Trusted Sources

Always pull your container images from trusted sources and publishers, or build and push then from your company in your own registry.

## Environment

### TODO_CODE - Keep Encryption Stack Up-To-Date

This is a duplicate of [Keep Your Software Up To Date](#todo_code---keep-your-software-up-to-date). However, encryption stack is so critical its update deserves its own rule.
