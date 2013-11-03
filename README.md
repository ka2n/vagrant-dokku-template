It's just dokku+vagrant template.

1. Create and start virtual machine

    vagrant up

2. Add SSH configuration to your host machine's ssh config

    vagrant ssh-config >> ~/.ssh/config

3. Add it as your project's git remote

    (In your project) git remote add dokku vagrant@192.168.34.10.xip.io:<projectname>

4. Push your branch to run app

    git push <your-branch> dokku

