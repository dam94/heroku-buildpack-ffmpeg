Heroku buildpack for ffmpeg
=======================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for using [ffmpeg](http://www.ffmpeg.org/) in your project.  
It doesn't do anything else, so to actually compile your app you should use [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi) to combine it with a real buildpack.

This is a static build of ffmpeg:
    
    ./configuration: --enable-gpl --enable-version3 --disable-shared --disable-debug --enable-runtime-cpudetect --enable-libmp3lame --enable-libx264 --enable-libx265 --enable-libwebp --enable-libspeex --enable-libvorbis --enable-libvpx --enable-libfreetype --enable-fontconfig --enable-libxvid --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvo-aacenc --enable-libvo-amrwbenc --enable-gray --enable-libopenjpeg --enable-libopus --disable-ffserver --enable-libass --enable-gnutls --cc=gcc-4.8

  libavutil      54.  7.100 / 54.  7.100
  libavcodec     56.  1.100 / 56.  1.100
  libavformat    56.  4.101 / 56.  4.101
  libavdevice    56.  0.100 / 56.  0.100
  libavfilter     5.  1.100 /  5.  1.100
  libswscale      3.  0.100 /  3.  0.100
  libswresample   1.  1.100 /  1.  1.100
  libpostproc    53.  0.100 / 53.  0.100

Usage
-----
To use this buildpack, you should prepare .buildpacks file that contains this buildpack url and your real buildpack url.  

    $ cat .buildpacks
    https://github.com/dam94/heroku-buildpack-ffmpeg.git
    https://github.com/heroku/heroku-buildpack-nodejs.git

The first build pack is the git URL to this repo.
The second build pack is for a Nodejs app.

You can verify installing ffmpeg by following command.

    $ heroku run "ffmpeg -version"
