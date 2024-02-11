# 29th-August-2007-Client-Execution

This repo will be covering the 2007 client that MaximumADHD put on GitHub.

https://github.com/MaximumADHD/Roblox-2007-Client

# The PDB path.

![PDB](https://raw.githubusercontent.com/MakeSureDudeDies/29th-August-2007-Client-Execution/main/PDB_Path.png)

# The compilation date.

On the PDB path we see a date, however IDA Pro detects a different date.

**Fri Aug 31 17:19:10 2007**

# Execution

We can use the string "Unable to create a new thread for %s. It did not execute" to find a subroutine/function that has all we need.

By going into it (sub_541120, ImageBase: 0x400000) we can see the whole execution process.

sub_540380 seems to be a function that gives us all the globals. Later lua_newthread is called, that thread is used as the lua state of every single lua c api function of in the sub_541120. We can see that eventually luaL_loadbuffer gets called to load the code on the stack. It's used in a if statement.

# The argument of the sub_540380 function

I believe that this argument is the Script Context.
