Before you start configuring your Windows build system, be aware of our tested configurations:
    Memory: You will need at least 2GB RAM, 4GB strongly recommended.
    CPU: Multiple CPUs are strongly recommended. 
      A build can take over an hour.
    Visual Studio 2017/2022 Community Edition.

Ensure you can build a stock viewer-development try as described in the SL wiki. Before asking for any help
compiling Firestorm, make sure you can build the Second Life viewer first. If you try and skip this step, you may
receive much less help. https://wiki.secondlife.com/wiki/Build_the_Viewer_on_Windows

If you want to use licensed FMOD or KDU build libraries (they are optional) you have to provision these yourself.
If you're licensing these with Phoenix/Firestorm, ask for the libraries for fmod and kdu. Put them into:

        c:\cygwin\opt\firestorm

If you're a community builder, you'll need to build these libraries yourself, then change your autobuild.xml file to
point to your own versions, or create a different autobuild.xml with your customizations, and use this with autobuild
instead of our default autobuild.xml There are some examples of how to build FMOD on the LL Wiki and opensource-dev
mailing list. We've created a non-KDU build target to make this easier. Everywhere you see "ReleaseFS" below, use 
"ReleaseFS_open" instead. This will perform the same build, using OpenJpeg instead of KDU.


To build Firestorm - a more detailed instruction can be found at https://wiki.firestormviewer.org/fs_compiling_firestorm_windows:

Open a CMD shell and navigating to your firestorm code repo:

        autobuild build -A 64 -c ReleaseFS

Other build targets you may use are:

    ReleaseFS (includes KDU, FMOD)
    ReleaseFS_open (no KDU, no FMOD)
    RelWithDebInfoFS_open (no KDU, no FMOD)

Other examples:
        autobuild configure -A 64 -c ReleaseFS                    # basic configuration step, don't build, just configure
        autobuild configure -A 64 -c ReleaseFS -- --clean         # clean the output area first, then configure
        autobuild configure -A 64 -c ReleaseFS -- --chan Private-Yourname   # configure with a custom channel

        autobuild build -A 64 -c ReleaseFS --no-configure              # default quick rebuild

If you want to set custom configuration, do this in the configure step separately from build, then run "autobuild
build -A 64 -c ReleaseFS --no-configure" as a secondary step.


Logs:
    Look for logs in build-vc1x0-64/logs

Output:
    Look for output in build-vc1x0-32/newview/Release
