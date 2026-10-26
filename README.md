curl -m 5 -sS -o /dev/null -w "%{http_code}\n" http://192.168.0.105:8765/


/usr/libexec/ApplicationFirewall/socketfilterfw --getglobalstate
/usr/libexec/ApplicationFirewall/socketfilterfw --getblockall