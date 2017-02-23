How to create a warning message to prevent pushing to Master
===

So we've all been there, worrying about pushing to master by accident, thankfully git provides a great set of features called `hooks`, these essentially are points in time when carrying out `git` commands that you can preset certain actions occuring e.g. do something before you commit or after you push etc. 

One great use case for this feature is avoiding unwittingly pushing to master. To that end you can create a `pre-push hook`. 

### Create a Pre-push hook in your local project

A pre-push hook does what the name implies it carries out an action which we will specify before a push occurs. Now these actions I've described are run via *shell scripts* (wait don't panic it'll be fine). A shell script is just a piece of code that runs in your terminal...

#### Configuring your project

1. Navigate (`cd .git`) into the `.git` folder in your project root directory (assuming you haven't got your folder elsewhere?!, yes the magic one we never look inside).

2. Inside it there should be a folder called hooks, `cd` into it and run `touch pre-push`. N.B. there are loads of great examples in here of hook scripts that you can run at different stages e.g. pre-commit, post-commit etc, Please read the comments before implementing these.

3. Inside of this file paste the following

```
    #!/bin/bash

    protected_branch='master'  
    current_branch=$(git symbolic-ref HEAD | sed -e 's,.*/\(.*\),\1,')
    
    if [ $protected_branch = $current_branch ]  
    then  
        read -p "You're about to push master, is that what you intended? [y|n] " -n 1 -r < /dev/tty
        echo
        if echo $REPLY | grep -E '^[Yy]$' > /dev/null
        then
            exit 0 # push will execute
        fi
        exit 1 # push will not execute
    else  
        exit 0 # push will execute
    fi
```

4. For those of you curious what this is and what the heck it's doing, it's a bash (as in the shell) script which sets master (as in the master branch) to a variable, checks if you on it with an if/else and if you are it prints a message and accepts a y in turn to push.

5. Once this file is created you will need to run the command `chmod +x pre-push` (**From within the hooks folder**). This last command tells your terminal to give this script permission to run this code.

### Configuring this setting globally
So now we've got this great feature in a local repo, but what if you want to do this all the time. Pushing to master is often a pretty big deal and even if it's not, we should all get in the habit of creating a branch per feature so master is always deployable. So..


1. `cd ~` To take you to your home folder run the command `git config --global init.templatedir '~/.git-templates'`. This tells your git config that when you initialize a repo it should make the files or folders you specify.

2. Next we run the command `mkdir -p ~/.git-templates/hooks/`. This will create a template hooks folder with the scripts you specify in it in every .git file you create. Fun fact the p flag i.e. `-p` tells the `mkdir` command to create all the necessary parent folders leading up to the one you actually want.

3. Then you can either copy the `pre-push` script from wherever you've made it or make a new one `touch pre-push` and copy the code from above into it.
4. Finally you should give the script permission to run as we did above using `chmod a+x ~/.git-templates/hooks/pre-push`.

5. You can then run git init in an existing repo to update it (without deleting any existing hooks).

