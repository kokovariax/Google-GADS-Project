**IN THIS CODE PROJECT, WE CREATE TWO VIRTUAL MACHINES IN DIFFERENT LOCATIONS AND CONNECT THE TWO**

#To display a list of all the zones in the region to where you are or closest to, enter this partial command gcloud compute zones list | grep followed by the region that Qwiklabs or your instructor assigned you to.

#Choose a zone from that list other than the zone to which Qwiklabs assigned you. For example, if Qwiklabs assigned you to region us-central1 and zone us-central1-a you might choose zone us-central1-b.

```
gcloud compute zones list | grep us-central1
```

#To set your default zone to the one you just chose, enter this partial command gcloud config set compute/zone followed by the zone you chose.

```
gcloud config set compute/zone us-central1-a
```

#To create a VM instance called desired-vm-one-name in that zone, execute this command:
```
gcloud compute instances create "desired-vm-one-name" \
--machine-type "n1-standard-1" \
--image-project "debian-cloud" \
--image "debian-9-stretch-v20190213" \
--subnet "default"
```

#TO close

```
exit
```
**Repeat the above process with another VM name (desired-vm-two-name) but in another zone within your Region.**







**TO CONNECT THE TWO VMS**

*#In the Navigation menu (Navigation menu), click Compute Engine > VM instances.

#You will see the two VM instances you created, each in a different zone.

#Notice that the Internal IP addresses of these two instances share the first three bytes in common. They reside on the same subnet in their Google Cloud VPC even though they are in different zones.

#To open a command prompt on the desired-vm-two-name instance, click SSH in its row in the VM instances list.

#Use the ping command to confirm that desired-vm-two-name can reach desired-vm-one-name over the network:*

```
ping desired-vm-one-name
```


#Notice that the output of the ping command reveals that the complete hostname of desired-vm-one-name is desired-vm-two-name.c.PROJECT_ID.internal, where PROJECT_ID is the name of your Google Cloud Platform project. GCP automatically supplies Domain Name Service (DNS) resolution for the internal IP addresses of VM instances.

#Press Ctrl+C to abort the ping command.

#Use the ssh command to open a command prompt on desired-vm-one-name:


```
ssh desired-vm-one-name
```


#If you are prompted about whether you want to continue connecting to a host with unknown authenticity, enter yes to confirm that you do.

#At the command prompt on desired-vm-one-name, install the Nginx web server:


```
sudo apt-get install nginx-light -y
```


#Use the nano text editor to add a custom message to the home page of the web server:

```
sudo nano /var/www/html/index.nginx-debian.html
```


#Use the arrow keys to move the cursor to the line just below the h1 header. Add text like this, and replace YOUR_NAME with your name:


```
Hi from YOUR_NAME
```



#Press Ctrl+O and then press Enter to save your edited file, and then press Ctrl+X to exit the nano text editor.

#Confirm that the web server is serving your new page. At the command prompt on desired-vm-one-name, execute this command:


```
curl http://localhost/
```


#The response will be the HTML source of the web server's home page, including your line of custom text.

#To exit the command prompt on desired-vm-one-name, execute this command:


```
exit
```


#You will return to the command prompt on desired-vm-two-name

#To confirm that desired-vm-two-name can reach the web server on desired-vm-one-name, at the command prompt on desired-vm-two-name, execute this command:


```
curl http://desired-vm-one-name/
```


#The response will again be the HTML source of the web server's home page, including your line of custom text.

#In the Navigation menu (Navigation menu), click Compute Engine > VM instances.

#Copy the External IP address for desired-vm-one-name and paste it into the address bar of a new browser tab. You will see your web server's home page, including your custom text.
