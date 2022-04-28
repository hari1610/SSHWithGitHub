# How to use SSH with GitHub

### Step 1
##### check if you have existing ssh key
- Open git bash
- Enter `ls -al ~/.ssh` to see existing ssh keys
- If any of the following key is displayed then you already have github key.
- If you dont then you have to generate the key

##### Generating a new ssh key
- open git bash
- using keygen a ssh key could be generated:
```bash
$ ssh-keygen -t ed25519 -C "your_email@example.com" 
# -t ed25519 is the type of encryption being used
# under your email enter your github email
```
- then you will be prompted with where to save the key. If you ar ehappy with the location just press enter
- now will be asked for a passphrase for the ssh, however this is optional and you can skip it.

##### Add the key to the ssh-agent
- Ensure the ssh agent is running:
```bash
# start the ssh-agent in the background
$ eval "$(ssh-agent -s)"
```
- you should get agent pid as output `Agent pid 59566`
- add the ssh private key you created to the ssh-agent:
```bash
$ ssh-add ~/.ssh/id_ed25519
```
##### Add the ssh key to your github account
- log into your github
- the ssh key you generated should also have a public key with the extension .pub
- copy the key inside that file.
- go to your github settings and go to the Access section
- now add the ssh key
##### Test your SSH connection
- open git bash and attempt to connect to github:
```bash
$ ssh -T git@github.com
```
- Verify that the resulting message contains your username