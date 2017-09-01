# Build package

## Create build structure

Not implemeted create it manually

### Package structure

- Directory
  - Definition.json
  - lib
    - libarke.a
    - libarke.so
  - include
    - arke
      - arke.hxx
      - wrapper.h

#### Package definition : *Definition.json*

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
            "path" : "libarke.so"
          },
         {
           "path" : "libarke.a"
         },
         ...
       ]
     },
    {
      "name" : "include",
      "types" : ["HEADERS"],
      "files" : [
        {
          "path" : "arke/arke.hxx"
        },
        {
         "path" : "arke/wrapper.h"
        },
        ...
      ]
    },
    ...
  ]
}
```

## Build package from structure

Go to package structure and launch build command

```sh
> arke package build
```

For next sample, this will create an archive name named **arke_arke_1.2.3_Linux-amd64-Ubuntu-1017.arke"
