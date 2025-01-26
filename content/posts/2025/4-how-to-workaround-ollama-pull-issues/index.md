---
title: "How to workaround Ollama models pull issues"
date: 2025-01-26
categories: 
- Howto
tags:
- ollama
- models
- pull
- issues
- issue
- macos
- bug
- workaround
slug: "how-to-workaround-ollama-pull-issues"
description: "Recent versions of Ollama have some issues pulling models from registry. Here is how to workaround it."
image:
---

In the past couple of days I was having this annoying **issue** while trying to pull a model from **[Ollama](https://ollama.com)**: I was running the command `ollama pull deepseek-r1:8b`, it was downloading something like 4-5% of the model and then **the connection was reset**, the client was "crashing" and **it always restarted from 0%**.

It looks like I wasn't alone: [https://github.com/ollama/ollama/issues/8406](https://github.com/ollama/ollama/issues/8406)

**Note**: I'm running Ollama `0.5.7`, it's likely they will fix the issue in one of the next releases.

## Solution

Someone kindly posted a [workaround](https://github.com/ollama/ollama/issues/8535#issuecomment-2613241807) which is a bash script able to invoke Ollama client and resume the download where it was left (Ollama client should to that, but it's not doing it correctly when it crashes).

Save this script in a file like `ollama-pull.sh` and make it executable with `chmod +x ollama-pull.sh`:

```bash
#!/bin/bash

die(){
  echo "$1"
  exit 1
}

#DRYRUN=echo

_=$(command -v jq) || die "Need jq"
_=$(command -v curl) || die "Need curl"

[ -z "$1" ] && die "usage: $0 modelname"

name=${1%%:*}
[[ "$1" = *:* ]] && tag="${1##*:}" || tag=latest

OLLAMA_MODELS=${OLLAMA_MODELS-/usr/share/ollama/.ollama/models}

cd $OLLAMA_MODELS || die "Couldn't cd to OLLAMA_MODELS ($OLLAMA_MODELS)"
[ ! -d blobs -o ! -d manifests ] && die "Missing blobs or manifests directory"
manifest_dir="manifests/registry.ollama.ai/library/$name"
[ -e "$manifest_dir/$tag" ] && die "$name:$tag already exists"
[ ! -d "$manifest_dir" ] && { $DRYRUN mkdir -p "$manifest_dir" || die "Couldn't mkdir manifest dir ($manifest_dir)" ; }

manifest=$(curl -sL https://registry.ollama.ai/v2/library/$name/manifests/$tag) || die "Couldn't fetch manifest"
errors=$(jq -cn "$manifest |.errors")
[ "$errors" = "null" ] || die "$errors"

config=$(jq -rn "$manifest | .config.digest") || die "No config digest"

$DRYRUN curl -#L -C - -o blobs/${config/:/-} https://registry.ollama.ai/v2/library/$name/blobs/$config || die "Couldn't fetch config blob"

for layer in $(jq -rn "$manifest | .layers[].digest") ; do
  $DRYRUN curl -#L -C - -o blobs/${layer/:/-} https://registry.ollama.ai/v2/library/$name/blobs/$layer || die "Couldn't fetch layer"
done

[ -n "$DRYRUN" ] && echo "echo '$manifest' > '$manifest_dir/$tag'" || { echo "$manifest" > "$manifest_dir/$tag" || die "Couldn't write manifest" ; }
```

and run the script in this way:

```shell
OLLAMA_MODELS=~/.ollama/models ./ollama-pull.sh deepseek-r1:8b
```

(replace `deepseek-r1:8b` with the `name:tag` of the model you want to pull)
