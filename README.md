[![Stories in Ready](https://badge.waffle.io/Parabot/Parabot.png?label=ready&title=Ready)](https://waffle.io/Parabot/Parabot)
[![Build Status](https://travis-ci.org/Parabot/Parabot.svg?branch=master)](https://travis-ci.org/Parabot/Parabot)

# 8/21/2024:
This fork has the internal API and the launcher, so they don't need to be grabbed from maven the way the original was designed. This fork also doesn't rely on the parabot website, which means no logging in or automatically pulling a list of public servers. 

If you want to use this parabot, you will have to find the hooks for your own servers. Here's a tutorial https://parabot.atlassian.net/wiki/spaces/TUTORIALS/pages/2981896/How+to+hook+a+server. 

Once you find the hooks and put them in an .xml, you can add the server to your parabot server folder at documents/parabot/servers/ by making a <servername>.json with the following format:
```
{
    "name": "<server name>",
    "author": "<doesn't matter>",
    "version": "<doesn't matter>",
    "client-class": "<whatever the classname for your Client interface was in your hooks, for example, 'Game'",
    "locations": {
        "provider": "https://2006scape.org/Downloads/bot/Provider.jar",
        "server": "<website link to the .jar download for the server",
        "hooks": "<link to your hooks.xml, preferably in a github like https://raw.githubusercontent.com/<your github username>/<repository>/main/hooks.xml ",
    }
}
```
example: 2006scape.json
```
{
    "name": "2006scape",
    "author": "RedSparr0w",
    "version": 1.0,
    "client-class": "Game",
    "locations":{
        "provider": "https://2006scape.org/Downloads/bot/Provider.jar",
        "server": "https://2006scape.org/Downloads/client.jar",
        "hooks": "https://raw.githubusercontent.com/crispycritter99/stuff/main/2006Scape_hooks.xml"
    }
}
```

I do not know Java. What I made has worked for me, but if it doesn't work for you, I probably won't be able to help you. 
# Parabot

Parabot V2.8.1

#### Links

[Website](http://www.parabot.org/)

[Download latest version](http://v3.bdn.parabot.org/api/bot/download/client)

#### Compilation
Build the project with the Maven POM file to have all required libraries installed.

#### Automation
Every stable build is automatically generated from the last commits of the master branch. This will take the version from both the `pom.xml` and the version in `.travis.yml`.

The nightly builds are automatically created from the last commits of the development branch. This will take the version from both the `pom.xml` and the version in `.travis.yml`, together with the build ID from travis.

#### Issues
If you've an issues regarding the bot itself, please report them [here](https://github.com/Parabot/Parabot/issues).

#### Maven
To add the client as a library, you'll first have to add our repository to your `pom.xml`:

```
    <repositories>
        <repository>
            <id>git-parabot</id>
            <name>Parabot's Git based repo</name>
            <url>https://maven.parabot.org/</url>
        </repository>
    </repositories>
```

Then you'll need to add the dependency:

```
    <dependencies>
        <dependency>
            <groupId>org.parabot</groupId>
            <artifactId>client</artifactId>
            <version>2.8.1</version>
        </dependency>
    </dependencies>
```

#### Labels
Labels are created with [GHLabel](https://github.com/jimmycuadra/ghlabel), whereas the yml is located in the .github directory
