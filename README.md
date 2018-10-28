# the-mission

the mission: a photo essay static site

uses the wonderfully simple [expose](https://github.com/Jack000/Expose)
static site generator

## quick start

### step 1: install expose 

start by installing expose (static photo essay site generator)
somewhere on your system:

```
cd /tmp
git clone git@github.com:Jack000/Expose.git expose
cd expose

# one time alias:
alias expose=${PWD}/expose.sh

# permanent alias:
echo "alias expose=${PWD}/expose.sh" >> ~/.bashrc
```

### step 2: prepare for deployment

Now prepare to deploy this site by preparing to deploy to the `gh-pages` branch. 

This step is optional.

If you have already pushed to the `gh-pages` branch:

```
cd expose
git clone -b gh-pages git@github.com:charlesreid1/the-mission _site
```

Optionally, if you haven't set up the `gh-pages` branch yet:

```
cd expose
git clone git@github.com:charlesreid1/the-mission _site
cd _site
git checkout --orphan gh-pages
rm -fr *
echo '<h2>hello world</h2>' > index.html
git add index.html && git commit index.html -m 'init commit' && git push origin gh-pages
```

### step 3: make site

From the `expose/` directory, run the `expose` alias command:

```
expose
```

This will generate the static site into `_site`.

### step 4: host site and serve locally

To serve the site locally, run a lightweight HTTP web server
using Python from the `_site` directory:

```
cd _site
python -m http.server 8001
```

Now open <http://localhost:8001> in a browser window to test
the site and make sure it looks good.

### step 5: push to deploy

When you're happy with the site, deploy to the `gh-pages` branch:

```
rm -fr _site/*
expose
cd _site/
git add -A . && git commit -a -m 'Update site content on gh-pages branch' && git push origin gh-pages
```




