# nimlz4
Nim wrapper for LZ4

## Installation
> nimble install https://github.com/SeaniaTwix/nimlz4

then apply `requires "nimlz4 >= 0.2.0"` to your `.nimble` file

## Simple compression (block API)
Use this API when you don't care about interoperability and assume only
this wrapper will be used to compress and decompress strings

**not tested**

## Frame compression (auto-framing API) - Tested
Use the frame API when you want your compressed data to be
decompressable by other programs.
```nim
import nimlz4

when isMainModule:

  var prefs = newLZ4F_preferences()
  var s = "tasntrlsdntransotidnpasrdpgsadransotidnpasrdpgsadransotidnpasrdpgsadransotidnpasrdpgsadransotidnpasrdpgsadgrndsalrgnyosaigynhoadsrynhadsroo"
  var compressed = compress_frame(s, prefs)
  var decompressed = uncompress_frame(compressed)
  echo compressed # "M`@�F�tasntrlsdntransotidnpasrdpgsad9�grndsalrgnyosaigynhoadsrynhadsroo
  echo decompressed # tasntrlsdntransotidnpasrdpgsadransotidnpasrdpgsadransotidnpasrdpgsadransotidnpasrdpgsadransotidnpasrdpgsadgrndsalrgnyosaigynhoadsrynhadsroo
```
