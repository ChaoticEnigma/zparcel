# ZParcel

ZParcel is a library and tool for adding typed resources to a custom archive file format.
Goals include low size overhead and fast fetching of single objects, identified by a 128-bit UUID.

### Compiling

Built with CMake:

    mkdir zparcel-build
    cd zparcel-build
    cmake ../zparcel
    make

## Usage

Create an empty parcel

    zparcel <file> create

List parcel contents

    zparcel <file> list

Store a new object in parcel, where *id* is a UUID or "time" or "random", *type* is { uint, sint, float, uuid, blob, string, list, file }, and value is a type-dependent string representation.

    zparcel <file> store <id> <type> <value>

Fetch the value of an object to stdout

    zparcel <file> fetch <id>

Show info about an object

    zparcel <file> show <id>

### Example

    $ zparcel data.parcel create
    OK - Create data.parcel

    $ zparcel data.parcel store aed31427-72ac-47c9-8abc-66082c7148b7 string "test zparcel string"
    OK aed31427-72ac-47c9-8abc-66082c7148b7

    $ zparcel data.parcel show aed31427-72ac-47c9-8abc-66082c7148b7
    UID: aed31427-72ac-47c9-8abc-66082c7148b7
    Lookup Time: 1.1949e-05 sec
    Type: string
    Data: zparcel test string

    $ zparcel data.parcel fetch aed31427-72ac-47c9-8abc-66082c7148b7
    zparcel test string

