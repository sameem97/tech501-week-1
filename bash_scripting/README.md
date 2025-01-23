## Key Commands

### Update

- To fetch latest package list using apt package manager:

```bash
sudo apt update
```

### Upgrade

- To install the latest package list fetched from update command:

```bash
sudo apt upgrade -y
```

### Install Nginx

- To install nginx web server:

```bash
sudo apt install nginx
```

### Check nginx status

- To view nginx PID:
  
```bash
sudo systemctl status nginx
```

### Restart Nginx

- After making any changes to Nginx, need to restart it to activate the changes:

```bash
sudo systemctl restart nginx
```

### Enable Nginx

- Enabling Nginx refers to automatically turning nginx on whenever the VM itself is turned on:

```bash
sudo systemctl enable nginx"
```

## Backup the Default Nginx Webpage

- The webpage is a html file stored in:
  
```bash
/var/www/html
```

- To backup the webpage you need to create a copy of the file:

```bash
e.g. sudo cp index.html index.html.bak
```

## Replace the default nginx webpage

- You can amend the contents of the `index.html` file to change the content and layout of the default nginx webpage.
- In my case, I changed it to "welcome to my custom webpage!" greeting, with a farewell message at the end.

## Add image to the nginx webpage

- cd into the html directory
- Download image onto the VM using wget command

```bash
cd /var/www/html
wget https://example_image.com/path-to-your-image.jpg
```
