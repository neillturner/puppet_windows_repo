# puppet_windows_repo

Very simple puppet repository to demonstrate using kitchen-puppet with windows and vagrant.
All it does is echo 'hello world' but useful for verifying an installation of kitchen puppet.

## Installation

1. Install Vagrant, Virtualbox and Ruby 2.x on your windows machine.

2. Run bundler to install all the ruby gems required.


## Check everything installed

In a command window in the puppet_repo directory run command

```
kitchen list

Should see response:
Instance                Driver   Provisioner  Verifier  Transport  Last Action
default-windows-2012r2  Vagrant  PuppetApply  Busser    Winrm      <Not Created>
```
## Create the virtual machine

First time it downloads the vm so will take 10 mins or so.

```
kitchen create default-windows-2012r2 -l debug
```
## Run Puppet
```
kitchen converge default-windows-2012r2 -l debug

Should see the hello world message successfully run:
       Notice: hello, world!
       Notice: /Stage[main]/Helloworld/Notify[hello, world!]/message: defined 'message' as 'hello, world!'
       Notice: Finished catalog run in 0.02 seconds
       Finished converging <default-windows-2012r2> (0m41.46s).
```
## Destroy the virtual machine.
```
kitchen destroy default-windows-2012r2
```