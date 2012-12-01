# bin

some little simple utilities i wrote and use a lot. not much more than a poor line of sh.

most of them are bad news. most os x specific too which is gross.

i guess they are all GPL 3 or later.

in the examples below, `pbcopy` and `xclip` both copy their input to ur clipclopboard

## randommac
for OS X, get a random mac address. if the last argument is `assign` it also assigns that to `en0`. using sudo. ugliest thing here.

#### usage:
`randommac [interface] [assign]`

## png2uri
Just takes a png file and spits out a datauri for it. pretty bad.

### usage:

`png2uri <file>` or `cat <file> | png2uri`

i like to use it like this:

`png2uri Pictures/gf3/dinosaur.png | pbcopy` 

*or*

`png2uri img/gf3-dinosaur.png | xclip`

## 2uri
This is the same thing really except it tries to guess the mime-type, so it can be used to make data URIs out of anything. can't pipe into this one. It uses `file` for magic.

code here actually isn't all that bad. it has error checking and i might actually even admit writing this one to a lady in the street.

### usage:
`2uri <file>`

i like to use it like this:

`2uri notebooks/divya.txt | pbcopy` 

*or*

`2uri img/paul_irish/dreamy/9001.jpg | xclip`


## geturl
This takes a file, sha1sums it, makes the sha1sum result the filename (gives it its extension back), rsyncs it to ur server with a bit of `-zL`, and prints a url it can be found at to `STDOUT`.

When somebody downloads it they can test it by making sure `shasum $file` lists the same thing twice, lal.

You need to give it a file argument. Not a directory, just a file. Any file. It will follow symlinks. So you can use this with [annexed](http://git-annex.branchable.com/) files or whatevz.

Next arg is ur server, this can be `chee@☂` or `10.20.30.5` or just `lol.org`.

Next arg is the document root on ur server, like `/srv/www/rightfulmillionairport.biz/public` or `web` if it's in ur `~`.

Next arg is the urlroot. That's like `https://snaekandchips.com/uploads`.
If it doesn't get this argument it tries to guess it like an idiot by just taking the last directory of `root` and sticking it on the end of `server` and sticking `http://` on the start. WFM.

I advise just editing the file and sticking ur info in the `_server` and `_root` and `_urlroot` near the top.

### usage:
`geturl <file> [server] [root] [urlroot]`

i like to use it like this:

`geturl coldhead\ in\ the\ pool\ jpegs.zip snaek.org /www/snaek.org/public/resources | pbcopy`

*or*

`geturl CLDHDP~1.MOV snaek.org /www/snaek.org/public/resources | xclip`

*or, if i've __edited the config file__*

`geturl branyen_riding_horse.jpg > txt/list_of_branyen_horse_riding_resources.txt`

---

PS: if you don't have an alias set up like this:

```
alias cx="chmod +x"
```

Then you aren't living life to the foolest.
I meant to type "fullest" just now, but that typo is even truer.

Live life to the foolest.
