# OPI - A Package Index for FOAM Projects

OPI is a package index for FOAM projects.
It has the goal to simplify discovery and installation of community based packages.

# Adding your Package

Adding a package to the index is simple.
Fork this repository, and add the package meta data as a json file to `pkg/<your_package>/<your_package>.json`.

An example is given below

```
{
    "name": "ogl",                             # required
    "repo": "github.com/hpsim/OGL.git",        # required
    "description":"GPU capable linear solver", # A short description to print in CLI max 80 chars
    "type": "lib",                             # optional, possible values: [lib,app] 
    "build":  # required, how to build the package, possible values ["wmake", "cmake", ["list of steps"]]
      ["cmake --preset release", "cmake --build --preset release", "cmake --build --preset release --target install"],
    "version": [">=2304", "<8"],               # optional, required FOAM version possible format examples: [  2304, 8, 0.1.0]  
    "keywords": ["GPU", "linear solver"]       # optional keywords for searching and grouping e.g. turbulence, scheme
}
```

# Usecases

Based on this package index we can build a package manager that can automatically resolve depencies, allows virtual environments for case studies with different package versions.

# [Optional] Index badge in your README

We encourage you to add a badge in your README referencing the index entry for your package.

As an example, dynamic JSON badges from [shields.io](https://shields.io/badges/dynamic-json-badge) can be useful, set:
- `url` to the raw JSON file you PR'd, eg. `https://raw.githubusercontent.com/exasim-project/opi/refs/heads/main/pkg/ogl/ogl.json`
- `query` to `$.[name,type,version]` for example (optional fields will be ignored if not present)
- `label` to `OPI`
- `labelColor` to `#0cc8cf` and `color` to `#131d36`

You can then paste the link to the badge into your README file, it will look like this:

![Dynamic JSON Badge](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fexasim-project%2Fopi%2Frefs%2Fheads%2Fmain%2Fpkg%2Fogl%2Fogl.json&query=%24.%5Bname%2Ctype%2Cversion%5D&style=for-the-badge&label=OPI&labelColor=%230cc8cf&color=%23131d36&link=https%3A%2F%2Fgithub.com%2Fexasim-project%2Fopi)

# Limitations

Currently, no interdependencies between packages or specific environment constraints are considered. 
