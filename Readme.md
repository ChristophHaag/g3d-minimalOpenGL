# What

Example code from  http://casual-effects.blogspot.com/2016/03/opengl-sample-codeand-openvr-sample-code.html is not available anymore via svn.

# How

With google I found a copy on some webserver. Downloaded it with

    wget -r -np -nH --cut-dirs 3 https://casual-effects.com/g3d/G3D10/samples/minimalOpenGL/

and fixed it.

# Yes, but I mean how do I use it

I added openvr as a submodule, so you need to git clone with --recursive and download ~250mb of data for it. Sorry. You really only need `headers/openvr.h` and `openvr/bin/linux64/libopenvr_api.so`, the rest is baggage and old git history.

    git clone --recursive https://github.com/ChristophHaag/g3d-minimalOpenGL.git
    mkdir build
    cd build
    cmake ..
    make
    ./minimalOpenGL

On other operating systems than Linux you should look into CMakeLists.txt and add the appropriate paths in `link_directories()` or something. Probably also need to do something with header paths for glfw or so.
