Just a note. Since git 1.8.5.2, two commands will do:

                git rm -r the_submodule
                rm -rf .git/modules/the_submodule

As @Mark Cheverton's answer correctly pointed out, if the second line isn't used, even if you removed the submodule for now, the remnant .git/modules/the_submodule folder will prevent the same submodule from being added back or replaced in the future. Also, as @VonC mentioned, git rm will do most of the job on a submodule.

###  --Update (07/05/2017)--

Just to clarify, the_submodule is the relative path of the submodule inside the project. For example, it's subdir/my_submodule if the submodule is inside a subdirectory subdir.

### Remove section

As pointed out correctly in the comments and other answers, the two commands (although functionally sufficient to remove a submodule), do leave a trace in the [submodule "the_submodule"] section of .git/config (as of July 2017), which can be removed using a third command:

git config -f .git/config --remove-section submodule.the_submodule 2> /dev/null