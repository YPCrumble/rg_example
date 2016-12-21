```
# Based on my experience with ag/ack
# I expect any of these to return all six files
# but return nothing in ripgrep.
rg -g file --files
rg -g dir --files

# This returns the list of files I expect.
# I think it's OK. A convenience function to make
# it quicker to type would be ideal (I'd be happy to
# create a PR for this if helpful!)
rg -g file* --files

# If the above returns the list of files I expect, why doesn't this?
# It appears I would need to know where in a long path the `dir*` exists...
rg -g dir* --files

# ...so this is weird, why does this return only subdir2's files?
# There are two odd things here. First, if dir* returns nothing then
# to me subdir* should also return nothing. 
# Second, why is it ignoring subdir1?
rg -g subdir* --files

# This is odd to me - these only return dir1/file2.txt and dir1/file3.txt.
# Why not file1.txt?
rg -g dir*/** --files
rg -g dir*/* --files

# This only returns two files:
rg -g dir*/**/* --files  # Returns dir2/subdir2/file2.txt and dir2/subdir2/file3.txt
# I would think it should also return dir2/subdir2/file1.txt

***
# It also means that I need to know the depth at which the files I want to search are,
# or am I missing something? That is usually not possible.
***

# I can't figure this out - why does this only return two of the three files in dir1?
rg -g dir1/file* --files  # returns only file2.txt and file3.txt

```
