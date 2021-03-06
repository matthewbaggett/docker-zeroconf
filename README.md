
# docker-zeroconf

This images demonstrate minimal ZeroConf using python-zeroconf library.

Two containers are created with one listening and the other looping on register/unregister.

The python samples running in images are copied from [python zeroconf github pages](https://github.com/paulsm/pyzeroconf).

This repository matches the kalemena/zeroconf docker hub image.

This sample registers and unregisters containers every 20s.


# How-To

## Build

```bash
$ docker-compose build
```

## Run

```bash
$ docker-compose up
```

## Scale

```bash
$ docker-compose scale registrator=10
```

# Sample output

```bash
$ docker-compose logs -f
Attaching to dockerzeroconf_browser_1, dockerzeroconf_registrator_1
browser_1      | 
browser_1      | Browsing services, press Ctrl-C to exit...
browser_1      | 
browser_1      | Service ead0029abd57 Test Web Site._http._tcp.local. of type _http._tcp.local. state changed: ServiceStateChange.Added
browser_1      |   Address: 172.24.0.2:80
browser_1      |   Weight: 0, priority: 0
browser_1      |   Server: ead0029abd57.local.
browser_1      |   Properties are:
registrator_1  | ('Number of arguments:', 1, 'arguments.')
browser_1      |     name: ead0029abd57
registrator_1  | ('Argument List:', "['registration-loop.py']")
browser_1      | 
registrator_1  | hostname = ead0029abd57
browser_1      | 
registrator_1  | ip = 172.24.0.2
registrator_1  | Registration of a service, press Ctrl-C to exit...
registrator_1  | Registering ead0029abd57...
registrator_1  | Unregistering ead0029abd57...
browser_1      | Service ead0029abd57 Test Web Site._http._tcp.local. of type _http._tcp.local. state changed: ServiceStateChange.Removed
registrator_1  | Registering ead0029abd57...
browser_1      | Service ead0029abd57 Test Web Site._http._tcp.local. of type _http._tcp.local. state changed: ServiceStateChange.Added
browser_1      |   Address: 172.24.0.2:80
browser_1      |   Weight: 0, priority: 0
browser_1      |   Server: ead0029abd57.local.
browser_1      |   Properties are:
browser_1      |     name: ead0029abd57
browser_1      | 
browser_1      | 
registrator_1  | Unregistering ead0029abd57...
browser_1      | Service ead0029abd57 Test Web Site._http._tcp.local. of type _http._tcp.local. state changed: ServiceStateChange.Removed
```

# References

https://pypi.python.org/pypi/zeroconf

http://stackoverflow.com/questions/1916017/simplest-way-to-publish-over-zeroconf-bonjour

https://vshivam.wordpress.com/2015/02/17/multicast-dns-service-discovery-in-python/

