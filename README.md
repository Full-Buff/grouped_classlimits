# grouped_classlimits
TF2 Server Plugin that implements grouped class limit configs

This can be layered on top of the already existing tournament mode commands for setting individual class limits, such as:
[tf_tournament_classlimit_scout](https://developer.valvesoftware.com/wiki/List_of_Team_Fortress_2_console_commands_and_variables)

With this plugin, you can name you custom grouped limit configs what ever you would like, and then name the group itself anything relevant. Finally, you define the player limit on the group, and the classes that limit applies to.
Custom configs are to be formatted as [KeyValue](https://wiki.alliedmods.net/KeyValues_(SourceMod_Scripting)) files.

Here is an example config, a more thorough version of which can be found in this repo.
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
