# Understanding Syntax
## Types of Variables
**Variables** are individual values that are stored to the player to manipulate their ingame experience. Without variables, creating any sort of story or event within the game would be impossible.

There are four types of variables. They are different in function, and when they should be reset.

### Variables

Name | Code | Description
------------|-------------|-------------
**Variables** | var | Variables are reset after the game is reloaded by the user.
**Map Variables** | mapvar | Map Variables are reset after the user switches maps.
**Event Variables** | ev | Event Variables are stored indefinitely. Due to their permanent nature, these values are used for events and story progression.
**Region Variables** | var/mapvar/ev | A variable controlled within region parameters, and are set at the initialisation of a region.

!!! warning "Using Var/Mapvar/EVs in Debug Mode"

    Be careful when using event variables within the sandbox/debug environment. The more variables that you load onto a player, the more data that may be wasted. To be safe, we advise that when testing that you use other types of variables first, and then switch them to even variables when the map goes public.

### Naming Variables
The most important thing with regard to variables is their name. Since variables are stored to the user as different values, no two triggers within the same region can have the same name. Sure, variables and map variables that are not permanent, may not matter as much as event variables, but any naming conflicts will still cause different values to be overwritten at the wrong times. This may potentially break any coded event for the player. Whilst ev’s,var’s and mapvar’s are locked to a region, it is still advised that the following naming scheme is used for your variables.

For naming variables and map variables, begin by using your three-letter region identification code as a prefix for your variable. For example; Otopo would be ```oto_``` This will automatically keep your variable exclusive to your maps to avoid naming discrepancies. Next, you should include the name of the map if it is a variable or map variable. Lastly, include a short, one-word identifier for what your variable does in the game. For example…
