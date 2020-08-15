# Tensorflow Wasm SIMD

There isn't much to document here, but I'll do my best.

The work done so far has been almost entirely in SIMDe. 

I wrote a little script that will do the compilation using emcc and emar, etc,
and downloaded simde, and placed that into the downloads directory here.

To find the intrinsics I was missing, I originally ran something like

`grep "v\([^_]+\)_\([usf])\([0-9]+\)(" ${find lite} > out` and then process
that file further in vim, with sort, uniq, etc.

Afterwards, I'd implement those intrinsics.

Finally, I started running the compilation, and from there, I would simply grep
through the output for `undefined identifier` or something similar, and I'd
then add that to the list of intrinsics. It's doing this that I was running
into most of the problems, and I have a feeling it may have been due to my not
using emmake/emcmake for the compilation. 

I made some changes to `neon_check.h` to check for compilation under wasm,
which would then include the simde header. This wouldn't be needed now with the
new emscripten integration.

Otherwise, that's pretty much it. 
