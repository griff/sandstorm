## How to view these docs

https://docs.sandstorm.io/

## How to edit these docs

Run the following.

```
# Get "dot" so we can render inline dot/graphviz
sudo apt-get install -y graphviz virtualenv
cd ~/projects/sandstorm
virtualenv tmp/docs-virtualenv
tmp/docs-virtualenv/bin/pip install mkdocs==1.0.4
tmp/docs-virtualenv/bin/pip install mkdocs-markdown-graphviz==1.3
tmp/docs-virtualenv/bin/mkdocs serve
```

Then visit http://localhost:8000/

## How to add images to the docs

In quick bullet points:

- You can add images to the docs.

- Look for examples of Markdown image syntax. For example, `docs/administering/faq.md`

- Set the IMG SRC to point at whatever URL you like, preferably a Sandstorm
  static publishing URL that you own.

- When your pull request gets merged, @paulproteus will copy them to a Davros
  grain he controls on oasis.sandstorm.io.

The reason for all this is that images can bloat a git repository a lot, so
for now, we don't store the images the main Sandstorm git repo.

## How to deploy to docs.sandstorm.io

- Ask Asheesh to share a particular GitWeb Pages grain with you. It's
  located on https://alpha.sandstorm.io/.

- Do a `git clone` of that repository into a directory, like:

```
git clone https://my_repo@alpha-api.sandstorm.io/ tmp/sandstorm-docs
```

- Run `generate.sh` to re-generate the docs, then commit them to this git repo.

```
PATH=$PWD/tmp/docs-virtualenv/bin:$PATH bash docs/generate.sh -d tmp/sandstorm-docs
```


- Run `generate.sh` with the `-p` flag to actually push them to the live site.

```
PATH=$PWD/tmp/docs-virtualenv/bin:$PATH bash docs/generate.sh -d tmp/sandstorm-docs -p
```
