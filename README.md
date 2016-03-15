# atlassian-vagrant

A modified Atlassian Vagrantfile to automatically start a product such as Confluence or Jira. Please read
the [developing locally](https://developer.atlassian.com/static/connect/docs/latest/developing/developing-locally.html) page
to better understand how this works.

This is built as an example that could be utilized in other projects. The Vagrantfile and provided scripts demonstrate how
to start a specific Atlassian product. It will:

  * Accept the Oracle license
  * Start your desired product in a screen
  * Check for the port to open
  
# Usage

The checked in Vagrantfile will use shell provisoner to execute "start-confluence.sh".  We have also provided a start-jira.sh. If you
want to run jira, edit Vagrantfile, comment out the start-confluence.sh line and uncomment the start-jira.sh line. Technically, you
can run both products at the same time. You can add scripts for other Atlassian products and run as many as you like, limited only by
the VM's memory.

**START:**

    vagrant up
    
In my testing, it takes about 5 minutes after the VM boots up the first time for either Confluence or Jira to become available.

**STOP:**

    vagrant halt
    
If you plan to use the VM again in the future, simply halt it. The created VM will still exist, but remain powered down.

**RESTART:**

    vagrant up
    vagrant provison
    
When you restart the VM, your screen and application will not be running. You will have to start it again using the provision command.
You can run `vagrant provision` anytime you modify the Vagrantfile or the start* scripts. The provided scripts check first to see
if the VM is listening on a port. If it is, the script exits without performing any action.

**DESTROY:***

    vagrant destroy
    
When you want to get rid of the VM, `vagrant destroy` will power it off completely and delete the virtual drive from disk.

