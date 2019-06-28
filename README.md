
# IOS XR Telemetry Proto Plugin for 65x

This repository contains plugin file for 65x release that can be used with collectors at
[telemetry-go-collector](https://github.com/ios-xr/telemetry-go-collector) to
unmarshal gpb messages.

Its generated using script provided at [telemetry-proto-go-plugins](https://github.com/ios-xr/telemetry-proto-go-plugins).
Due to size contraints a different repo is used for plugin file.

## Usage instructions:
Download dialin or dialout collector from [telemetry-go-collector](https://github.com/ios-xr/telemetry-go-collector) 
and use -plugin option when collector is started to point to plugin .so
file from this repository.

Example:
Dailin to router grpc port 57500 for subscriptions red-info and mem and use gpb encoding:
telemetry-go-collector/bin/telemetry_dialin_collector -server 192.168.122.62:57500 -username *** -password *** -plugin plugin_65x.so -subscription red-info#mem -encoding gpb
Start grpc server at port 57500 and expect to receive gpb encoded message:
telemetry-go-collector/bin/telemetry_dialout_collector -port 57500 -plugin plugin_56x.so -encoding gpb

