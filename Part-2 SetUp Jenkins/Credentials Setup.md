1. **SonarQube**

    - We will generate and set sonarQube token in jenkins

    - To generate the toke we need to login onto sonarQube server and head to administartion page then click on security and users as show below 

![alt text](image.png)

    - Now you can see the users and a column named Tokens click on that and generate a new token that and copy it and store it.
    - After we have generated the token we would now go back to jenkins and head to Dashboard -> Manage Jenkins -> Credentials. Click on global and go to add credentials. Select secret text and fill in the token we got in the step above.

2. **Docker Hub**

    - You would need to setup your docker hub account cerdentails. To do this following the following steps

    - Now go to jenkins and head to Dashboard -> Manage Jenkins -> Credentials. Click on global and go to add credentials. Select Username with password and fill the username and password and save it.

3. **k8-user Creation and Cred**
    - Here we need to create a service account that would be responsible to access the k8s cluster and deploy applications on it.
    - Visit the following page and create a service account https://kubernetes.io/docs/reference/access-authn-authz/service-accounts-admin/#create-token, and copy the ymal file and apply it by specifying for which namespace you want to create the service account.
    - We will have to assign/bind this user to a role so that it has all the necessary permissions to run.
    - If you don't know how to define a role there would a ymal file for that and to bind it to a role.
    - Now we would need to copy the sceret for this user. Below is the command for that.
    ```
    kubectl describe secret <your secret name> -n <your namespace>
    ```
    - Now copy this secret and go to jenkins and head to Dashboard -> Manage Jenkins -> Credentials. Click on global and go to add credentials with the kind being secret text and paste the secret we got in the step above.

4. **Mail Cred Generation**
    - For this go to manage your google account and under security goto two step verification and at the end you can go to App Passwords and create a new app password.
    - Now configure this in jenkins under credentials and kind should be username with password where the password would be the one you generated right now.
    
