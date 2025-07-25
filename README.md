<p align="center"><a href="https://github.com/thecoder-001/MineColab"><img src="https://github.com/thecoder-001/MineColab/blob/master/Logo.png" alt="Logo" height="80"/></a></p>
<h1 align="center">MineColab</h1>
<p align="center">Run Minecraft Server on Google Colab</p>
<a href="https://colab.research.google.com/github/thecoder-001/MineColab/blob/master/MineColab.ipynb" target="_parent"><img align="right" src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"></a>

## :hear_no_evil:  First of all, what is google Colab?
As the official FAQ says, colaboratory, or “Colab” for short, is a product from Google Research. Colab allows anybody to write and execute arbitrary python code through the browser, and is especially well suited to machine learning, data analysis and education. More technically, Colab is a hosted Jupyter notebook service that requires no setup to use, while providing free access to computing resources including GPUs.
In short, it is a vm provided for learning, running python code, machine learning or for general purpose.
## :moneybag:  Is it really free to use?
Yes, Colab is free to use. But there are some points which, according to me one should keep in mind:
1. Though colab is a free service, it shouldn't be exploited indiscriminately or without any care. One should value that its a resource offered for no cost and can get depleted/restricted if the demand increases out of control.
2. If it isn't obvious, one shouldn't run mission-critical services (like large and important servers/databases/python programs) on it. Its resources are not guaranteed and not unlimited, and the usage limits sometimes fluctuate. Also, the notebook has a maximum runtime of 12 hours, after which, it should be manually restarted.
3. If you need to use it pretty often for intensive tasks, consider purchasing a vps server. A heavy increase in server load would force google to close the service.

In the end, it is just my personal opinion and can be ignored safely. Just ask your heart whats right and whats wrong. Also, please try to use it as a once in a while resource and not 24x7 so that others can avail the free resources too.

## :page_with_curl: Instructions
1. Open the notebook in google colab.
3. Read through the notebook, most of the code is self explanatory. Run the cells which are useful for your use-case.
4. Run the first cell which runs the Minecraft server.
5. Now you have three options. You can either use ngrok, playit.gg or cloudflare's argo. Ngrok is easy to setup and doesn't requires anything to be installed by the clients but it can often be quite unreliable. Argo doesn't have such limitations but requires a bit more work. Playit.gg's implementation is unpolished at the moment (debug log spam) but offers convenient static subdomains.
  * Ngrok:
    Change `tunnel_service` variable and follow the prompts.
  * Cloudflare argo:
    1. After running the first cell,`Your free tunnel has started! Visit it <tunnel_address>` would be logged in the notebook console.
    2. Download [Cloudflared client](https://github.com/cloudflare/cloudflared/releases/) on all the client machines.
    3. Now on your local machine, launch the binary with `./cloudflared-linux-amd64 access tcp --hostname <tunnel_address> --url 127.0.0.1:25565`
    4. Finally, connect to `127.0.0.1:25565` from your minecraft client.
  * Playit.gg:
    Change `tunnel_service` variable, ignore the debug output _(todo:fix)_ and follow the prompts.

## :zap:  So, how does it actually work?
As Google Colab is a VM running Ubuntu server as base OS, it can be easily used as a Minecraft server. Here are the steps which the notebook performs to setup the server:
1. Update the system's apt cache.
2. Install Openjdk-16 (Java) through apt-get.
3. Mount Google Drive to access the minecraft folder (Drive is used here to provide persistent storage).
4. Setup Argo/ngrok/playit Tunnel (Opening a tunnel at port 25565) depending on the `tunnel_service` variable.
5. Change directory to the minecraft-server folder on google drive ("Minecraft-server" is the default, located in the root directory of my Google Drive.)
6. List/Print the file list on the screen to indicate succesful directory change.
7. Startup the Minecraft server (with optimized JVM parameters from [Aikar's guide)](https://aikar.co/2018/07/02/tuning-the-jvm-g1gc-garbage-collector-flags-for-minecraft/)

## 🐛 Found a bug?
Report report the bug by creating a new issue and use this helpful [issue template](https://github.com/thecoder-001/MineColab/issues/new?assignees=&labels=bug&template=bug_report.md&title=%5BBUG%5D).
 
Or suggest a new feature using this [template](https://github.com/thecoder-001/MineColab/issues/new?assignees=&labels=enhancement&template=feature_request.md&title=%5BFeature+Request%5D).

## 👍 Tips
- If something does not work, try using a VPN like [windscribe](https://windscribe.com) before opening an issue.
- Switch between the three different tunnel providers and see which works best for you.
- Make regular backups of your world.

[![ForTheBadge built-with-love](http://ForTheBadge.com/images/badges/built-with-love.svg)](https://github.com/thecoder-001)

IS FORK OF REAL PROHECT AND ALL CREDIT GOES TO thecoder-001 and its project is recountinued by me if any errors found please notify
