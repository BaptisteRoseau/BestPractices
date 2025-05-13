# Security

Nothing is inherently secure in IT. However, things can be made harder to attack.

These set of rules help making an attack harder.

## Generalities

### SRTG001 - Consider Everything Already Hacked

Always consider that the application you are writing, the container you are building or the node you are setting up is already hacked.

What information does the attacker have access to ? Credentials ? Encrypt them. Open port ? Close them. Root access ? Run as a user. Writing permissions ? Differentiate owner and executor of source files.

By considering everything already hacked, you can clearly see what needs additional security measures. Fix them.

### SRTG002 - Use Minimal Permissions

You should always give minimal permissions whether in the production environment or the CI/CD tooling and organization member accesses. Avoid duplication, and if a reorganization is required, reorganize.

A drawback of this rule is that access management can become unbelievably hard, and a pain to work with. Find the right trade off for your team.
This can be overcome by using standards, containers or tools like OAuth to avoid manual management.

### SRTG003 - Keep Your Software Up To Date

There is a tremendous amount of new vulnerabilities found every day. Those vulnerabilities are often patched rapidly so you should always keep your software up to date to make sure those vulnerabilities are patched.

## Executables

### SRTX001 - Strip Executables

Use the `strip --strip-all` command to remove all the symbols documentation and reduce the executable size.

### SRTX002 - Use Obfuscation

Obfuscate your code when possible using specialized tool for your language.

For example, for a web page's javascript, bundle your code using Vite. This will both obfuscate the code and reduce its size.

### SRTX003 - Remove Symbol Addresses

When using `readelf` or `nm`, a user should not be able to see the address of the symbols within an executable.

This avoids attacks based on symbols address offset.

## Containers

Containers are a great part of today's IT environment. Making sure they are secure is very important.

`nonroot` distroless containers with statically linked compiled stripped executables are great for production environment, whereas CI containers can be less secure but pulled or built from trusted sources.

### SRTC003 - Avoid Using `root` User

For production containers, you should always run as a non-root user.

Specify the `USER` instruction in the `Dockerfile` and make sure the files have minimal permissions required by this user.
Read-only files should be owned by root to prevent any modification.

### SRTC003 - Make Executables Read-Only

Make sure the executables files have only `r-x` permissions for the user executing the code.

The executables can either be owned by another user or by `root`.

### SRTC003 - Use Minimal Dependencies

Never include unused dependencies within a container. More dependencies means more potential vulnerabilities.

### SRTC003 - Use An Entrypoint With Default Command

Always specify an `ENTRYPOINT` in the `Dockerfile` with a default `CMD`.

### SRTC003 - Consider Every Layer Is Into The Final Image

Every layer of a container image is stored and cached.

This means that if secrets or files are copied into the image and then removed, they remain in the layer.

Hence, anyone can access it even if it is not in the final image. Never add sensitive files or source code within the final container.

To avoid this issue, use [multi-stage image building](https://docs.docker.com/build/building/multi-stage/).

### SRTC003 - Use Trusted Sources

Always pull your container images from trusted sources and publishers, or build and push them from your company's own registry.

## Environment

### SRTE001 - Keep Encryption Stack Up-To-Date

This is a duplicate of [Keep Your Software Up To Date](#srtg003---keep-your-software-up-to-date). However, encryption stack is so critical its update deserves its own rule.

Next: [Project Management](./project_management.md)
