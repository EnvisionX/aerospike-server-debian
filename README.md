# Specs for building DEB package with Aerospike Server

Adapted to Debian 8 Jessie.

## HowTo

1. Clone Aerospike (latest version is 3.7.3):

```
git clone --recursive --branch $VERSION https://github.com/aerospike/aerospike-server.git
```

2. Create origin tarball:

```
tar czf aerospike-server_$VERSION.orig.tar.gz aerospike-server
```

Note the ``.git`` subdirectory must be tar'ed as well.

3. Copy ``debian`` directory to the cloned ``aerospike-server`` dir.

4. Create package with sources:

```
dpkg-source -b aerospike-server
```

5. Build the binary package from the sources:

```
pbuilder aerospike-server_$VERSION-$RELEASE.dsc
```

6. Add build artifacts to the APT repository:

```
reprepro include $SUITE_NAME aerospike-server_$VERSION-$RELEASE_$ARCH.changes
```
