# grouped_classlimits
TF2 Server Plugin that implements grouped class limit configs

This can be layered on top of the already existing tournament mode commands for setting individual class limits, such as:
[tf_tournament_classlimit_scout](https://developer.valvesoftware.com/wiki/List_of_Team_Fortress_2_console_commands_and_variables)

With this plugin, you can name you custom grouped limit configs what ever you would like, and then name the group itself anything relevant. Finally, you define the player limit on the group, and the classes that limit applies to.
Custom configs are to be formatted as [KeyValue](https://wiki.alliedmods.net/KeyValues_(SourceMod_Scripting)) files.

## Installation
Download the latest build of the plugin [here](https://github.com/Full-Buff/grouped_classlimits/releases/tag/latest) and place it in your './tf/addons/sourcemod/plugins/' directory on your server.
Then, download the example config [here](https://github.com/Full-Buff/grouped_classlimits/blob/main/grouped_classlimits.cfg), make any changes to it that you need for your custom limits, then place it in your './tf/cfg/' directory on your server. 
See below for making more custom configs and the commands to execute them ad-hoc.

Here is a shorter example config:
```
"GCL_Heavy-Med-Exclusive"
{
    "support_limit"
    {
        "limit"     "1"
        "classes"
        {                   // The value ("1") doesn't matter, only the key name is used.
            "medic"         "1"
            "heavy"         "1"
        }
    }
}
```

Loading this config will allow there to be either 1 heavy, OR, 1 medic. There can not be one of each on the same team. 

Custom configs can be placed in either ./tf/cfg/ or ./tf/addons/sourcemod/configs/

Keep in mind, custom config files can be named anything you would like, but will not be executed by default. 

## Cvars you should care about

### sm_grouped_classlimits_enabled
This is defaulted to 1, but can be set to 0, if you would rather not move the plugin to the disabled folder.

### sm_grouped_classlimits_config
This is defaulted to 'grouped_classlimits.cfg', but you can set it to whatever the name of your cfg file is. Plugin will check both locations for custom configs.


There is also sm_grouped_classlimits_immunity_flags, which is defaulted to 'b', the generic admin level. [Find more about the admin levels in sourcemod here.](https://wiki.alliedmods.net/Adding_Admins_(SourceMod)#Levels)

## Admin Commands you should care about

### sm_reload_classlimits
This reloads the currently selected config file.

### sm_load_classlimits <filename>
This loads a new config file bye taking the name of the file as an arugment. Here are some examples of using this command:

```
sm_load_classlimits grouped_classlimits

sm_load_classlimits grouped_classlimits.cfg

sm_load_classlimits gcl-heavy-med-excl
```

