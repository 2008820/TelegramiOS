## Edit by telegramd

### Introduce

Default connect to telegramd test server.

If you want to connect to your own server, you can modify the following code:

```
LegacyDatabase/TGShareContextSignal.m
L162
                        [mtContext performBatchUpdates:^
                        {
                            [mtContext setSeedAddressSetForDatacenterWithId:1 seedAddressSet:[[MTDatacenterAddressSet alloc] initWithAddressList:@[
                                // [[MTDatacenterAddress alloc] initWithIp:@"149.154.175.50" port:443 preferForMedia:false restrictToTcp:false cdn:false preferForProxy:false]
                                [[MTDatacenterAddress alloc] initWithIp:@"47.100.25.99" port:443 preferForMedia:false restrictToTcp:false cdn:false preferForProxy:false]
                            ]]];
			    ......

Telegraph/TGTelegramNetworking.m
L222
        if (_isTestingEnvironment)
        {
            [_context updateAddressSetForDatacenterWithId:1 addressSet:[[MTDatacenterAddressSet alloc] initWithAddressList:@[
                [[MTDatacenterAddress alloc] initWithIp:@"47.100.25.99" port:443 preferForMedia:false restrictToTcp:false cdn:false preferForProxy:false]
            ]] forceUpdateSchemes:true];
            [_context updateAddressSetForDatacenterWithId:2 addressSet:[[MTDatacenterAddressSet alloc] initWithAddressList:@[
                [[MTDatacenterAddress alloc] initWithIp:@"47.100.25.99" port:443 preferForMedia:false restrictToTcp:false cdn:false preferForProxy:false]
            ]] forceUpdateSchemes:true];
        }
        else
        {
            [_context performBatchUpdates:^
            {
                [_context setSeedAddressSetForDatacenterWithId:1 seedAddressSet:[[MTDatacenterAddressSet alloc] initWithAddressList:@[
                    [[MTDatacenterAddress alloc] initWithIp:@"47.100.25.99" port:443 preferForMedia:false restrictToTcp:false cdn:false preferForProxy:false],
	        .....
 
```

### Compile


### Feedback
Please report bugs, concerns, suggestions by issues, or join telegram group [Telegramd](https://t.me/joinchat/D8b0DRJiuH8EcIHNZQmCxQ) to discuss problems around source code.

