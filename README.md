# Star Wars Galaxies Unity Code (C++) Repository

This is the main server code for SWG Unity 1.0 as originally forked from source.  Please see that repository for original publication and alteration credit.

# Building

For local testing, and non-live builds set MODE=Release or MODE=Debug in the build.properties file in swg-main.

For production, user facing builds, set MODE=MINSIZEREL for profile built, heavily optimized versions of the binaries.

## Profiling and Using Profiles (IN-WORK)

To generate new profiles, build SWG with MODE=RELWITHDEBINFO. 

Add export LLVM_PROFILE_FILE="output-%p.profraw" to your startServer.sh file. 

WHILE THE SERVER IS RUNNING do a ps -a to get the pid's of each SWG executable. And take note of which ones are which.

After you cleanly exit (shutdown) the server, and ctrl+c the LoginServer, move each output-pid.profraw to a folder named for it's process.

Then, proceed to combine them into usable profiles for the compiler:

llvm-profdata merge -output=code.profdata output-*.profraw

Finally, then replace the profdata files with the updated versions, within the src/ tree.

See http://clang.llvm.org/docs/UsersManual.html#profiling-with-instrumentation for more information.

# More Information

Join the SWG Unity Discord if you would like to contribute: https://discord.gg/4GbJfuJtTT
