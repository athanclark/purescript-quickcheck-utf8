purescript-quickcheck-utf8
================================

> "Why do we need another QuickCheck generator for `String`?"

Because, when generating _any_ character (bitwise), there are some _surrogate control sequences_ that
aren't actually valid UTF-8, and in fact, if you try to "print" the generated string, stuff gets
_automatically_ converted for you - a difficult issue to debug, indeed!

You can read more about the issue in the [Surrogate section in the UTF-8 Wiki article](https://en.wikipedia.org/wiki/Universal_Character_Set_characters#Surrogates).

Mainly, this issue arose when designing [arraybuffer-class](https://pursuit.purescript.org/packages/purescript-arraybuffer-class),
and verifying that randomly generated strings have isomorphic `ArrayBuffer` encodings.
