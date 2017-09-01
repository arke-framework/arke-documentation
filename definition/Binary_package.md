# Binary package

## Package structure

A binary package is a **GZip** archive containing three files :

- Package
  - archive.tar.xz
  - archive.hash
  - archive.sign (optional)

### Archive : *archive.tar.xz*

Tar archive compressed with **XZ** containing all files

- Archive
  - **Package.json**
  - lib
    - libarke.so
    - libarke.a
    - ...
  - include
    - arke/arke.hxx
    - arke/wrapper.h
    - ...
  - ...

#### Package.json

```json
{
  "organization" : "arke",
  "name" : "arke",
  "version" : "1.2.3",
  "target" : {
    "os" : "Linux",
    "arch" : "amd64",
    "variants" : [
      "Ubuntu",
      "no-ssl"
    ]
  },
  "groups" : [
     {
       "name" : "lib",
       "types" : ["BINARIES"],
       "files" : [
          {
            "path" : "libarke.so",
            "hash" : "651381315123183513213843513813513813132138"
          },
         {
           "path" : "libarke.a",
           "hash" : "321651831513813581321386135135183213813813"
         },
         ...
       ]
     },
    {
      "name" : "include",
      "types" : ["HEADERS"],
      "files" : [
        {
          "path" : "arke/arke.hxx",
          "hash" : "189165165431385138161351351321313513201321"
        },
        {
         "path" : "arke/wrapper.h",
         "hash" : "3666941681351251351351321351351351351351351"
        },
        ...
      ]
    },
    ...
  ]
}
```

### Hash : *archive.hash*

Hash file containing SHA256 of the archive, used to validate transfert before installation
