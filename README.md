# enb-api
ENBSeries API, done in the style of TrueDirectionalMovement and other SKSE APIs

API should work for any xSE version, but only SKSE was "tested"

# Accessing the API

Register your plugin for SKSE messaging interface  
```
SKSE::GetMessagingInterface()->RegisterListener(MessageHandler);
```  
  
Request API on `kPostLoad`  
Store the API handle and re-use it

```
ENB_API::ENBSDK1001* g_ENB = nullptr;

void MessageHandler(SKSE::MessagingInterface::Message* a_msg)
{
	switch (a_msg->type) {
		case SKSE::MessagingInterface::kPostLoad:

			g_ENB = reinterpret_cast<ENB_API::ENBSDK1001*>(ENB_API::RequestENBAPI(ENB_API::SDKVersion::V1001));
			if (g_ENB) 
				logger::info("Obtained ENB API");
			else
				logger::info("Unable to acquire ENB API");

			break;
	}
}
```

# Using the API

All API functions have been documented.

Check `ENBSeriesAPI.h` for function definitions  
Check `ENBSeriesSDK.h` for type definitions (shared with ENBSeries)

Example
```
if (g_ENB)
  logger::info("Using ENB SDK version {}"sv), g_ENB->GetSDKVersion())
```


