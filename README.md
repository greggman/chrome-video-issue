Chrome-Video-Issue
==================

AFAICT, sometime after v47 this particular case stopped working

on a Retina OSX running 10.11.3

## Steps

1.  Install node.js

2.  Run these steps

        git clone https://github.com/greggman/chrome-video-issue.git
        cd chrome-video-issue
        ./setup-files.sh
        npm install http-server
        ./node_modules/http-server/bin/http-server

3.  Open Chrome, Open an incognito window (optional), go to `http://localhost:8080`,
    click on `chrome-video-issue.html`

## What's the expected output?

Something like

    http://localhost:8080/video2.mp4
    http://localhost:8080/video.mp4
    http://localhost:8080/aa-temp/video1.mp4
    http://localhost:8080/aa-temp/video2.mp4
    http://localhost:8080/aa-temp/video3.mp4
    http://localhost:8080/aa-temp/video4.mp4
    http://localhost:8080/aa-temp/video5.mp4
    http://localhost:8080/aa-temp/images/Scan001.jpg
    http://localhost:8080/aa-temp/images/Scan002.jpg
    http://localhost:8080/aa-temp/images/Scan003.jpg
    http://localhost:8080/aa-temp/images/Scan004.jpg
    http://localhost:8080/aa-temp/images/Scan005.jpg
    http://localhost:8080/aa-temp/images/Scan006.jpg
    http://localhost:8080/aa-temp/images/Scan007.jpg
    http://localhost:8080/aa-temp/images/Scan008.jpg
    http://localhost:8080/aa-temp/images/Scan009.jpg
    http://localhost:8080/aa-temp/images/Scan010.jpg

### What do you see instead

In general Chrome post 47 hangs around

    http://localhost:8080/video2.mp4
    http://localhost:8080/video.mp4
    http://localhost:8080/aa-temp/video1.mp4
    http://localhost:8080/aa-temp/video2.mp4
    http://localhost:8080/aa-temp/video3.mp4
    http://localhost:8080/aa-temp/video4.mp4

## Notes:

The app is loading 8 videos/images in parallel. You can change this line

    var maxParallelDownloads = 8;

to

    var maxParallelDownloads = 1;

To make it only load 1 at a time. In that case it will run intermittently. If it
succeeds just try refreshing the page a few times and it will likely fail




