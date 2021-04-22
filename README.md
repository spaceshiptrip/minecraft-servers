# minecraft server

## Spigot Server
1. To update server get the latest BuildTools.jar:
   ```
   curl -o BuildTools.jar https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar
   ```
1. Build it
   ```
   git config --global --unset core.autocrlf
   java -jar BuildTools.jar
   ```
1. Start the server in an independant shell:
   Start the server using `screen`:
   ```
   screen -AmdS spigot java -Xms3G -Xmx3G spigot.jar
   ```
   - OR -
   Start the server with `tmux`:
   ```
   tmux new -t spigot
   <enter into the tmux shell>
   java -Xms3G -Xmx3G spigot.jar
   ```

---


### Look into installing the sheller:
https://github.com/endofzero/Minecraft-Sheller

### Resource Packs:
https://thebreakdown.xyz/%EF%BB%BF15-resource-packs-for-minecraft/

### Installing Screen
1. Install the software "screen". You'll need this to let the Minecraft server run in the background later, so you can close the PuTTY window without causing the Minecraft server to stop. Use the following command for the installation: apt install screen -y
1. Now add a user who will run the Minecraft Server on your Linux server. Use the following command: adduser --disabled-login minecraft. In this example the user is called "minecraft". You can use a different name, but make sure to always use your own chosen user name instead of "minecraft" when you follow the next steps of this tutorial (e.g. "mcserver").
1. You can skip all further information such as the name, telephone number, etc. by pressing enter as well.
1. Now use the command su minecraft to switch to your Minecraft user.
1. Go to the home directory of this user by executing the command cd. The home directory is named exactly like the user himself and therefore the path is "/home/minecraft".
1. Then use the command wget https://cdn.getbukkit.org/spigot/spigot-1.15.2.jar to download the latest version of Spigot. If you want to use Craftbukkit, the command is wget https://cdn.getbukkit.org/craftbukkit/craftbukkit-1.15.2-R0.1-SNAPSHOT.jar.
1. After the download is completed, you should see the downloaded JAR file using the command ls.
1. Next, create a start and a stop script. These two scripts let you start and stop your Minecraft server later. To create the start script named "start.sh", use the command nano start.sh. Now the nano text editor opens. Here you need to enter the following command: screen -AmdS minecraft java -Xms4096M -Xmx4096M -jar /home/minecraft/spigot-1.15.2.jar. Make sure you enter the correct filename of your previously downloaded JAR file. Instead of "4096", you can specify the amount of RAM in MB that you want to reserve for your Minecraft server. Important: Keep enough memory for the system and other software running on your Linux server.
1. Now save the start script by pressing CTRL + X, then hit the "Y" key and press enter.
1. Now create the stop script as well by executing the command nano stop.sh. Within the nano editor you need to write the following command into your script: screen -r minecraft -X quit. Save the stop script just like the start script by pressing CTRL + X, then hit the "Y" key and press enter.
1. After that you have to assign execution permissions for these two scripts. You do that with the following command: chmod +x start.sh stop.sh
1. In order to be able to start the Minecraft server, you must first accept the license terms. To do this, execute the command echo "eula = true" > eula.txt. This creates a file which indicates that you accepted these license terms.
Then run the start script to start your Minecraft server. Use the command ./start.sh
1. To get into the Minecraft server console, you need to open the screen background process. To do this, execute the command screen -r minecraft. Under Debian 8 and Debian 9, however, you must execute the command script /dev/null before using the screen command. If you are logged in as the user "root", you must first switch to the Minecraft user by executing the command su minecraft. To exit the Minecraft server console, hold down the CTRL key and press the "A" and "D" keys one after the other.
1. Your Minecraft server is now ready to use. You can start and stop it at any time. Just log in as the Minecraft user by executing the command su minecraft, go to the Minecraft server directory using the command cd /home/minecraft and execute the start or stop script (./start.sh or ./stop.sh).

### Installing Spigot
1. Use the command wget https://cdn.getbukkit.org/spigot/spigot-<game version>.jar to download the latest version of Spigot.
1. Start Building Spigot, get BuildTools:
  ```
  wget "https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar" -O BuildTools.jar
  ```
1. Run the latest BuildTools.
  ```
  java -jar BuildTools.jar
  ```

#### Building Spigot
https://www.spigotmc.org/wiki/buildtools/


It's been nearly 40 days since our 1.8 builds were released, and in that time we have made around 240 releases, averaging around 5 a day. Great work and many thanks to all those who have contributed, and of course our other core developer Thinkofdeath.

I'd like to use this time to point out a number of resources which have emerged in the community, and also re-document the slightly simplified process of installing 1.8 (and also Mac OSX and JDK-less support for BuildTools). Without further ado, here are the new recommended requirements and instructions for using BuildTools to generate your server jars:

Requirements
Computer powerful enough to run Minecraft
1GB of free disk space.
2GB of memory, at least 1GB free. (Minimum for Minecraft).
Java 7 or Java 8 installed. (Recommended for Minecraft).
Git & Bash installed.
Installing Java
Minecraft only requires Java 6 to run, whilst BuildTools requires at least Java 7. Given that Java 6 was EOL'd in February 2013, all users are recommended to be running Java 7 or Java 8. If not you can download it for your platform from the Oracle Technology Network.

Linux users might find it easier to use their distributions package manager, the instructions for a few distributions are provided below.
Debian / Ubuntu:
Code (Bash):
sudo apt-get install openjdk-7-jre-headless
Ubuntu 14.10:
Code (Bash):
sudo apt-get install openjdk-8-jre-headless
RHEL/CentOS:
Code (Bash):
sudo yum install java-1.7.0-openjdk
Fedora 21:
Code (Bash):
sudo yum install java-1.8.0-openjdk
Installing Git
You need a tool named Git installed in order to download the server sources for compilation. On Windows, Git will also provide some other tools which would otherwise be unavailable for compilation. Fortunately Git is very easy to install, just follow the instructions on the Git Download Page.

Downloading and Running BuildTools
Open a shell.
Windows: Open an MSysGit Bash terminal. You can do this by clicking on the icon, or right clicking in an empty folder.
Mac OSX: Open the terminal application.
Linux: You know how to do this.
Download BuildTools.jar. There are a number of ways to download BuildTools, you could:
Download it straight from your browser by clicking this link.
Windows / Mac OSX / Most Linux: Use curl to download it:
Code (Bash):
curl "https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar" -o BuildTools.jar
Other Linux: Use wget to download it:
Code (Bash):
wget "https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar" -O BuildTools.jar
Run BuildTools:
Code (Bash):
java -jar BuildTools.jar
You're done! Check your folder for the server jars. Thanks for using CraftBukkit | Spigot.
To update your server, simply run BuildTools again. It is also recommended to update BuildTools.jar at least weekly.
If you have any issues, check the troubleshooting guide for help: http://www.spigotmc.org/wiki/buildtools/#troubleshooting-and-help

Changelog
In case you don't feel like trudging through Git commit logs, @Dead-i has created an awesome changelog. Check it out here: http://www.spigotmc.org/wiki/changelog/

RSS Feeds
You can also find RSS feeds with changelogs here: https://hub.spigotmc.org/jenkins/view/RSS/

Maven Repository
We now have a Maven repository up and running, for more info please see the wiki page: http://www.spigotmc.org/wiki/spigot-maven/

Wiki
Massive thanks to all those who have been working on the wiki. It would be great to get people to continue to help update the documentation and include some of the changes listed in this new guide. (No JAVA_HOME or MAVEN_OPTS anymore!). If you require access to a locked page, just leave a message on the discussion page and someone will set you up with access.


Thanks for your support through all of 2014 and we hope 2015 is equally awesome,
Long Live Spigot!

~Spigot Team
#1

## Whitelist
After server is setup, be sure to whitelist the people allowed to the servver:
```
Whitelist on - This activates the whitelist
Whitelist off - This disables the whitelist
Whitelist add playername - This will add a player to the whitelist
Whitelist remove playername - This will remove a player from the whitelist
Whitelist list - This will list the players who have been added to the whitelist
```


## Other Resources
* https://github.com/endofzero/Minecraft-Sheller
* https://aws.amazon.com/getting-started/hands-on/run-your-own-minecraft-server/




## Give Cheats
```
give spaceshiptrip netherite_sword{Unbreakable:1b,Enchantments:[{id:"minecraft:knockback",lvl:2},{id:"minecraft:sweeping",lvl:20s},{id:"minecraft:looting",lvl:20s},{id:"minecraft:smite",lvl:20s},{id:"minecraft:sharpness",lvl:20s}]} 2

give spaceshiptrip netherite_pickaxe{display:{Name:'{"text":"Epic Pickaxe","color":"gold","bold":true}'},Unbreakable:1b,Enchantments:[{id:"minecraft:efficiency",lvl:10s},{id:"minecraft:fortune",lvl:20s},{id:"minecraft:mending",lvl:1s}]} 2
```

```
give spaceshiptrip minecraft:diamond_sword{Unbreakable:1b,Enchantments:[{id:"minecraft:knockback",lvl:2},{id:"minecraft:sweeping",lvl:20s},{id:"minecraft:looting",lvl:10s},{id:"minecraft:smite",lvl:20s},{id:"minecraft:bane_of_arthropods",lvl:20s},{id:"minecraft:sharpness",lvl:20s}]} 6

give spaceshiptrip minecraft:diamond_pickaxe{display:{Name:'{"text":"Epic Diamond Pickaxe","color":"blue","bold":true}'},Unbreakable:1b,Enchantments:[{id:"minecraft:efficiency",lvl:10s},{id:"minecraft:fortune",lvl:20s},{id:"minecraft:mending",lvl:1s}]} 4

give spaceshiptrip netherite_pickaxe{display:{Name:'{"text":"Epic Pickaxe","color":"gold","bold":true}'},Unbreakable:1b,Enchantments:[{id:"minecraft:efficiency",lvl:10s},{id:"minecraft:fortune",lvl:20s},{id:"minecraft:mending",lvl:1s}]} 1
```

```
give spaceshiptrip minecraft:diamond_pickaxe{display:{Name:'{"text":"Epic Diamond Pickaxe","color":"blue","bold":true}'},Unbreakable:1b,Enchantments:[{id:"minecraft:efficiency",lvl:20s},{id:"minecraft:fortune",lvl:20s},{id:"minecraft:mending",lvl:1s}]} 2

give spaceshiptrip minecraft:diamond_shovel{Unbreakable:1b,Enchantments:[{id:"minecraft:efficiency",lvl:20s},{id:"minecraft:fortune",lvl:20s},{id:"minecraft:mending",lvl:1s}]} 1
```

```
give spaceshiptrip minecraft:crossbow{Unbreakable:1b,Enchantments:[{id:"minecraft:multishot",lvl:20s},{id:"minecraft:quick_charge",lvl:20},{id:"minecraft:mending",lvl:20s}]} 2

give spaceshiptrip minecraft:bow{Unbreakable:1b,Enchantments:[{id:"minecraft:infinity",lvl:20s},{id:"minecraft:power",lvl:20s},{id:"minecraft:mending",lvl:20s},{id:"minecraft:flame",lvl:20s}]} 2

give spaceshiptrip minecraft:bow{Unbreakable:1b,Enchantments:[{id:"minecraft:infinity",lvl:20s},{id:"minecraft:power",lvl:20s},{id:"minecraft:mending",lvl:20s}]} 2
```
```
**Epic Diamond Setup**
give spaceshiptrip minecraft:diamond_chestplate{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:thorns",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
give spaceshiptrip minecraft:diamond_helmet{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:thorns",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
give spaceshiptrip minecraft:diamond_leggings{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:thorns",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
give spaceshiptrip minecraft:diamond_boots{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:thorns",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
```


```
EPIC Nether Armor setup

# this remove the thorns on the armor so that you can get the drops
give spaceshiptrip minecraft:golden_chestplate{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
give spaceshiptrip minecraft:golden_helmet{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
give spaceshiptrip minecraft:golden_leggings{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
give spaceshiptrip minecraft:golden_boots{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6


# These next ones have thorns 
give spaceshiptrip minecraft:diamond_chestplate{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:thorns",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
give spaceshiptrip minecraft:diamond_helmet{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:thorns",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
give spaceshiptrip minecraft:diamond_leggings{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:thorns",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
give spaceshiptrip minecraft:diamond_boots{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:thorns",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6

give spaceshiptrip minecraft:golden_chestplate{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:thorns",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
give spaceshiptrip minecraft:golden_helmet{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:thorns",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
give spaceshiptrip minecraft:golden_leggings{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:thorns",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
give spaceshiptrip minecraft:golden_boots{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:thorns",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6

```
## Using Screen

```
screen -D -r minecraft
```

that detaches any running screens and reataches to `minecraft`



---

```
>give spaceshiptrip minecraft:netherite_chestplate{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
[08:37:01] [Server thread/INFO]: Gave 6 [Netherite Chestplate] to spaceshiptrip
>give spaceshiptrip minecraft:golden_helmet{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
[08:37:58] [Server thread/INFO]: Gave 6 [Golden Helmet] to spaceshiptrip
>give spaceshiptrip minecraft:netherite_helmet{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
[08:38:41] [Server thread/INFO]: Gave 6 [Netherite Helmet] to spaceshiptrip
>give spaceshiptrip minecraft:golden_leggings{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
[08:39:38] [Server thread/INFO]: Gave 6 [Golden Leggings] to spaceshiptrip
>give spaceshiptrip minecraft:netherite_leggings{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
[08:40:24] [Server thread/INFO]: Gave 6 [Netherite Leggings] to spaceshiptrip
>give spaceshiptrip minecraft:golden_boots{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
[08:41:16] [Server thread/INFO]: Gave 6 [Golden Boots] to spaceshiptrip
>give spaceshiptrip minecraft:netherite_boots{Unbreakable:1b,Enchantments:[{id:"minecraft:protection",lvl:40s},{id:"minecraft:mending",lvl:40s},{id:"minecraft:fire_protection",lvl:40s},{id:"minecraft:blast_protection",lvl:40s},{id:"minecraft:projectile_protection",lvl:40s},{id:"minecraft:respiration",lvl:40s},{id:"minecraft:aqua_affinity",lvl:40s}]} 6
```
