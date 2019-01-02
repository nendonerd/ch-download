# Download videos (course) from coursehunters.net

> the original repo has a bug which won't ignore already downloaded files, and no one is maintaining it anymore. This is a fixed version.

# How to install:

```sh
git clone https://github.com/nendonerd/ch-download.git
```

# How to use:

```sh
cd /path/to/ch-download
coursehunters -u course-url [-d dirname] [-l lessons] [-e email] [-p password]
```

for convenience, you can add an alias of the command to .profile(MacOS) or .bashrc(Linux)
```sh
alias hunt="/path/to/coursehunters -u"
```
then you can cd into the folder you want to put your download files, and run ```hunt <url>```

### Arguments:

```sh
-e: email for login
-p: password for login
-u, --url: https://coursehunters.net/course_name
-d, --dir: download folder, default <course_name>
-l, --lessons: download only listed lessons, e.g.: "1-5, 7, 10, 12-15" or 3-7,9,11,15-20
```

# Orignial repo:
[alekseylovchikov/ch-download](https://github.com/alekseylovchikov/ch-download)

# Some thoughts:
This app helps me a lot for downloading tutorials from coursehunters to learn. Thanks a lot to its authors.

As I'm in China, the internet is really slow during traffic time, downloading files will always result in stucking, which I have to terminate the command and run it again. But due to the bug, it will begin to download from scratch no matter how many files you have downloaded, which is really annoying. So I looked into the code and fixed it.

The code is using fs.createWriteStream() to download stuff. so it may not very efficient. I'm looking to extract the parse part of the code and just output the download url, then pipe into aria2.

Currently I'm using the app in a raspberry pi and a vps. For some courses, instead of using this app, you can find their magnet links on rutracker, then put them in 115wangpan or torrent downloader in vps to download them in maxium speed.