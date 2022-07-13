# Facebook Audience Network *GODOT Plugin compatible with godot >= 3.2.1 new plugin system*

## Facebook SDK Version
[dependencies]
    api ('androidx.annotation:annotation:1.0.0')
    api ('com.facebook.android:audience-network-sdk:6.+')
    
## Config

![autoload-facebook-ads](https://user-images.githubusercontent.com/14333871/178789209-4e76dd5d-4426-44e1-829e-996f3a47ebe0.png)

![register-modules](https://user-images.githubusercontent.com/14333871/178789232-8b8ce7f6-fb22-4031-ac96-247ffbc1a02e.png)

## Using the plugin

`clone` or download the repo to your and place GodotFAN folder to  `your_godot_project/android` folder   , after installing [Android Build Template](https://docs.godotengine.org/en/stable/getting_started/workflow/export/android_custom_build.html)

*the new Godot plugin system doesn't require compiling the source code*

![demo](/facebook-ads-example/demo.gif)

### Initialize the module
in your `project.godot` add 
```
[android]
modules="org/godotengine/godot/GodotFAN"
```
or From Project Setting >> Compression > Android

## API 
```python
var facebookAds
func _ready()-> void:
	facebookAds = Engine.get_singleton("GodotFAN")
	facebookAds.FacebookAdsInit(get_instance_id(),"YOUR_INTERSTITIAL_PLACEMENT_id","YOUR_REWARDED_VIDEO_PLACEMENT_id" , "YOUR_BANNER_PLACEMENT_id")
```

### Calling the interstitial and rewarded video ads

```python

facebookAds.showInterstitial() #Calls an interstitial ad

facebookAds.loadRewardedVideo() # Loads a rewardedVideo ad

facebookAds.showRewardedVideo() #Calls a rewarded video ad (remmember to call loadRewardedVideo() before showing a rewarded video)

facebookAds.loadBanner(isTop : bool) #Loads a banner AdView , it takes a bool parameter , true for banner in the TOP , false for a banner in the BOTTOM

facebookAds.showBanner() #show a banner ad if it is hidden , the banner ad is by visible by default

facebookAds.hideBanner() #hide a banner ad  , the banner ad is by visible by default 

```

## CallBacks

```python

#Interstitial Ad CallBacs

func onInterstitialReady() -> void:
	#Called When a interstitial Ad is loaded and Ready
	pass


func onInterstitialClosed() -> void:
	#Called When a interstitial Ad is closed
	pass

##Rewarded Video Ad CallBacs

func onRewardedReady() -> void:
	#Called When a Rewarded video Ad is loaded and ready
	pass

func onRewardedClosed() -> void:
	#Called When a Rewarded video Ad is closed (completed or not , this only detects the close action)
	pass

func onRewardedCompleted() -> void:
	#Called When An Rewarded video Ad is completed

	#Call Reward Function here
	pass


```

### Debugging

`adb -d logcat GodotFan:V FAN:V godot:V *:S`

*Tested with godot 3.4*
