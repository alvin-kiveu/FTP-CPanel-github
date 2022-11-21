# Auto Deploy Github Project into cPanel

Step 1 : Create an FTP account on your hosting provider

Step 2 : Go to the seting page on your repository and scroll down to the Secrete section on Action

Step 3 : Create a new Secrete and name it FTP_SERVER

Step 4 : Copy the password of your FTP account and paste it in the value section

Step 5 : Create another Secrete and name it FTP_USERNAME

Step 6 : Copy the username of your FTP account and paste it in the value section

Step 7 : Create another Secrete and name it FTP_PASSWORD

Step 8 : Copy the host of your FTP account and paste it in the value section

Step 9 : Go to actions and click on set up a workflow yourself

Step 10 : Copy the code below and paste it in the workflow file and save it as main.yml

```yml
name: Deploy to cPanel
on:
  push:
    branches:
      - main
jobs:
  FTP-Deploy-Action:
    name: FTP-Deploy-Action
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2.1.0
        with:
          fetch-depth: 2
      # Deploy to cPanel
      - name: FTP-Deploy-Action
        uses: SamKirkland/FTP-Deploy-Action@3.1.1
        with:
          ftp-server: ${{ secrets.FTP_SERVER }}
          ftp-username: ${{ secrets.FTP_USERNAME }}
          ftp-password: ${{ secrets.FTP_PASSWORD }}
```

Step 11 : Commit the changes and push it to your repository

Step 12 : Go to actions and click on the workflow file

Step 13 : Click on the run workflow button

Step 14 : Wait for the workflow to complete

Step 15 : Go to your FTP account and check if the files have been uploaded

Step 16 : If the files have been uploaded, go to your hosting provider and check if the website is live

Step 17 : If the website is live, you are done
