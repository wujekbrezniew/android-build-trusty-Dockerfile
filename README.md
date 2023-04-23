#Dockerfile for building android-build-trusty image.

Forked from here: https://android.googlesource.com/platform/build/+/master/tools/docker

With updated Python to match repo requirements.

#Build

The Dockerfile in this directory sets up an Ubuntu Trusty image ready to build a variety of Android branches (>= Lollipop). It‘s particulary useful to build older branches that required 14.04 if you’ve upgraded to something newer.


Copy your host gitconfig, or create a stripped down version:  
` $ cp ~/.gitconfig gitconfig `   
Then build image:   
` $ docker build --build-arg userid=$(id -u) --build-arg groupid=$(id -g) --build-arg username=$(id -un) -t android-build-trusty . `    

Then you can start up new instances with:   
` $ docker run -it --rm -v $ANDROID_BUILD_TOP:/src android-build-trusty `   
` cd /src; source build/envsetup.sh `   
` lunch aosp_arm-eng `  
` m -j50 `  
