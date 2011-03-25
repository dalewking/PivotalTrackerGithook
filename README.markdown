Pivotal Tracker Checkin comment githook
=======================================

This is a hook you can add to a git workspace to easily add story numbers from unfinished stories in the current iteration to your check-in comments (in the format described [here](https://www.pivotaltracker.com/help/api?version=v3#scm_post_commit_message_syntax)).

Coupled with proper SCM hooks to send commits to pivotal, this makes it easy for your check-in comments to appear in the comments for the story and to change the state of the story from the check-in.

When you invoke git commit and it opens the editor the message will include comment lines that look like this in the prepared message: 

    #[Fixes #12345678] This is the story description

Then you simply delete the # from any line that the checkin applies to and if the checkin does not complete the story also delete the word `Fixes` from the line.  

How to use
----------
* Edit the `prepare-commit-msg` file and enter your pivotal tracker API token and project number in the space indicated.
* Copy the `prepare-commit-msg` and `xsl` files to the `.git/hooks` directory of your workspace.

Note:
-----
Git hook scripts are local to your workspace and are not part of any commit. If you clone a new workspace you will have to copy the githook scripts manually to the new workspace.

This has been tested and is used on OSX. Will probably work on Linux as well if you have xsltproc installed. Support for anything besides OSX is left as an exercise for the reader.

