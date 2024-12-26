firstly you need to install the GDB software on you system, that depends on your OS.

#do not do optimization of the compile
./configure --enable-depend --enable-cassert --enable-debug  # add your private prefix
after the configure, edit the src/Makefile.global file, and find the CFLAGS variable, change the -O2 to -O0

# make sure you Postgresql process id, postgresql has init process and many sub processes
example: a simple way to debug backend process handling, use `psql postgres`, this will create a backend process, 
and type `select pg_backend_pid();` in the psql context, system will return the its process id, and use `sudo gdb attach <pid>` to attach the process
after attach the process, the psql will hang there, you must set your breakpoint and continue the process
