To use, first `stack install` and then add:
`
{-# OPTIONS_GHC -F -pgmF strip-ths #-}
`
to the top of any Template Haskell using file.

`strip-ths` will attempt to replace any Template Haskell splices with their dumped counterparts 
(via `ghc`'s `-ddump-splices` flag).

Expects `stack`, but you could switch the call to "stack" to a call to "cabal" in `app/Main.hs` 
and it should work fine.

*Notes
I build this to work around issues with GHC's built-in linker: it has problems compiling
any Template Haskell-using file that depends on a library that itself depends on DLLs.

See https://ghc.haskell.org/trac/ghc/ticket/10672 and related tickets.

See also ZeroTH, and Joey Hess's EvilSplicer 
(I wasn't sure either was maintained, and had a specific usage style in mind)

I've only tried this on 7.10.2 with `lens`'s `makeLenses` function thus far.
