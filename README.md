## Edit by telegramd


### 中文


##### 1.升级或下载 xcode

##### 2.git clone https://github.com/nebulaim/TelegramiOS

##### 3.git submodule update --init --recursive

##### 4.换掉配置文件(LegacyDatabase/TGShareContextSignal.m, Telegraph/TGTelegramNetworking.m)下的所有ip地址

##### 5.首先用 xcode build LegacyDatabase,然后再运行Telegraph

> 如果要清楚缓存，删除 `~/Library/Developer/Xcode/deriveData` 下的所有文件

### English


##### 1.download or update xcode
##### 2.git clone https://github.com/nebulaim/TelegramiOS
##### 3.git submodule update --init --recursive 
##### 4.change config files （LegacyDatabase/TGShareContextSignal.m, Telegraph/TGTelegramNetworking.m） all ip address
##### 5.first use xcode build LegacyDatabase and run Telegraph
> if clean xcode cache, delete `~/Library/Developer/Xcode/deriveData` Under the folder all files


#### Introduce

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

