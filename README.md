# 🐋 VerneMQ (Open Source Build)

This repository is a fork of [vernemq/docker-vernemq](https://github.com/vernemq/docker-vernemq) with one key change:

The Dockerfile has been modified to **build VerneMQ from source** instead of downloading prebuilt binary tarballs that require a paid subscription.

That means you can run VerneMQ entirely under its **Apache 2.0 license**, without hitting the subscription model.

---

## ✨ What’s different?

- **Original `docker-vernemq`:**  
  Downloads a precompiled VerneMQ binary tarball under EULA → requires a paid subscription.

- **This fork:**  
  Clones [vernemq/vernemq](https://github.com/vernemq/vernemq), runs `make rel` inside a build stage, and packages the result into a slim Debian runtime image.

No EULA, no subscription — just pure OSS VerneMQ.

---

## 🔨 Build the image

Clone this repo and build locally:

```bash
git clone https://github.com/<your-username>/docker-vernemq.git
cd docker-vernemq

# Build the image (no subscription required)
docker build -t my-vernemq:2.1.1 .
```

---

▶️ Run VerneMQ

```bash
Start a single-node broker with anonymous access enabled:

docker run -d --name vernemq \
  -p 1883:1883 \
  -p 8888:8888 \
  -e DOCKER_VERNEMQ_ALLOW_ANONYMOUS=on \
  my-vernemq:2.1.1
```

Check logs:

```bash
docker logs -f vernemq
```

---

⚠️ Notes

This fork is meant for OSS usage. If you prefer official, supported binaries, use the subscription-based images
.

Multi-arch builds (amd64 + arm64) can be done with docker buildx if you need portability.

---

📜 License

VerneMQ itself: Apache License 2.0

This Docker setup: same as upstream docker-vernemq
