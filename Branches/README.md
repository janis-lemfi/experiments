# Usage

## Preparation

At first make files executable

```sh
chmod +x old-branches
chmod +x delete-old-branches
```

It is good idea to put this folder into your path. If you will not add it
there, then you need to specify full link to executable script.

## Usage

At first you need to navigate to repository folder.

```sh
cd /path/to/my/project
```

Safe part - list remote branches and saving to file.

```sh
# Get list of old branches (3m+) in markdown table format, use
./old-branches

# To save it to file, use
./old-branches > report.md

# To get short list only with branch names, use
./old-branches short > report.txt

# you can use niceness off unix pipes to grep out something
./old-branches short \
  | grep -i "keyword" \ # this will take only branches that contain "keyword" in name
  | grep -i -v "unwanted" \ # this will leave everything that doesn't contain "unwanted"
  | head -n 10 \ # take only first 10
  > report.txt
```

Scary part - deleting list of branches

```sh
# delete all branches that are listed in generated short list file
./delete-old-branches path/to/report.txt
```
