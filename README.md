# Proxy_Signal
Simple Apple Automator script to run [Signal Desktop](https://github.com/signalapp/Signal-Desktop) (the secure chat app) with system proxy on Mac OS.

# What is this for
Unfortunately the desktop version of Signal on Mac OS still does not pickup the system proxy configuration properly. See related issue [here](https://github.com/signalapp/Signal-Desktop/issues/1632).

So if you find yourself in the situation where you have to use a proxy to connect to the Signal service, like behind a company network or in China, that's when you need it.

# How to use
1. Download the zip, extract it, open the package via Automator, test if it launches signal properly with proxy (it should connect).

| Open | Test |
| ---- | ---- |
| ![image](https://user-images.githubusercontent.com/24445006/132814474-3f831732-7251-4ad4-98f6-6287a59c741a.png) | ![image](https://user-images.githubusercontent.com/24445006/132816473-cd206a59-5a5e-4e10-b070-0e88f0150f3a.png)


_If it didn't workout, check your system proxy configs in System Preference->Network->Wifi/Ethernet->Advanced settings->Proxy, make sure proxy works, tweak or hardcode the proxy address if needed till it works._
 
 
2. Save this script as a standalone Automator Application: **File -> Convert To -> Application**, **File -> Export**. Now you should have a dedicated "App" that launches Signal with proxy.

| Convert to | Choose Application | Export |
| ---- | ---- | -----|
| ![image](https://user-images.githubusercontent.com/24445006/132814571-953e042d-f2a3-4161-add4-313e12c55125.png) | ![image](https://user-images.githubusercontent.com/24445006/132814592-755fc4fb-97fe-4110-a841-6beec49dc385.png) | ![image](https://user-images.githubusercontent.com/24445006/132816191-375fc554-6e6b-475d-8f25-4fc82b3e45bc.png)



3. Drag and Drop your newly created App to Application folder, whenever you need proxy, you launch from here.
![image](https://user-images.githubusercontent.com/24445006/132814662-1e970c31-7712-463f-b05d-f2e43a21f8e0.png)


# How it works
It really comes down to only 2 scripts of a total of 3 lines of code...

![image](https://user-images.githubusercontent.com/24445006/132812545-74ee3566-92f9-4a56-a1a1-49ea4a605307.png)


First script gets current system proxy address and port, save it as a result.

Second script takes the address and port, set the proxy and launches the signal App.

You can do this in pure shell, but Automator wraps it into a nice App package, just like an real App.


# Cases I didn't cover but should be workable
Now you get the whole idea, so if you are in a more complicated proxy configuation, like using PAC or your proxy requires authentication, you should tweak it yourself in the Automator app, I think it's quite self-explanatory. 

In the worst case senario, just drop the 1st script and hardcode proxy ip and port, it should do it anyway.


# Just for curiosity: Why Signal desktop App doesn't suport proxy?
Accoring to the random talks in several proxy related open issues, it seems the Signal App uses Chromium as its fundamental platform, this proxy issue is at the Chromium layer other than the actual with-in app layer, so the developers seem to have trobuble to deal with it without touching or modding Chromium. 

Apparantly most Signal develpers don't have this proxy problem, so it's not a pirority, I guess that's why it stays un-addressed till today. (I could be wrong it's just from my quick grasp I'm no expert here)
