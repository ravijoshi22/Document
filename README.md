# Setup Guide For Keycloak

1. [Download Keycloak](https://www.keycloak.org/downloads.html) and install it.
2. Start the keycloak server by running the _standalone.sh_ file
```
Root Directory of keycloak ---> bin ---> standalone.sh
```
3. Now login to keycloak administration console and navigate to your desired realm. You can add new realm by selecting **Add Realm** option.

![first](https://user-images.githubusercontent.com/42262807/44833485-dae89380-ac4b-11e8-8011-e1e8872f7bf9.png)

- Enter Realm Name and click on **CREATE** to add realm.

4. Now create ROLE. The Role will be used by your applications to define which users will be authorized to access the application. Click on the **Roles** left link and choose **Add Role**:

![second](https://user-images.githubusercontent.com/42262807/44834179-fce31580-ac4d-11e8-98f3-38a7f98ff90c.PNG) 

5. Now we need to users to realm who will be able to access the resources of realm. Click on the **Users** left option and choose to **Add a new User :--** 

![third](https://user-images.githubusercontent.com/42262807/44834839-e5a52780-ac4f-11e8-86b2-63cabe54a508.PNG)

6. After user is created following action needs to be performed on it :--

- Setting a password for it so click on **Credentials** and set a new Password for the user:

![fourth](https://user-images.githubusercontent.com/42262807/44835166-f3a77800-ac50-11e8-9872-ae7e5d13d2a4.PNG)

```
NOTE :-- Disabling Temporary will make user password permanent.
```
-  Now we need to map user to a role. Click on **Role Mappings** and assign the user desired role  by selecting that role and clicking on **add selected**:

![5](https://user-images.githubusercontent.com/42262807/44835454-df17af80-ac51-11e8-8a74-be96df7120ce.PNG)

7. Now we need to create groups . Click on the **Groups** left option and choose **New** to create a new group.

![6](https://user-images.githubusercontent.com/42262807/44835889-133fa000-ac53-11e8-98ff-d7ed74c0a8d3.PNG)

8. Next step is to assign user into group. Select **Users** from left options and select the user whom you want to add in group. Choose _Groups_ option from tab and then select the _group-name_ and click on **join**.

![7](https://user-images.githubusercontent.com/42262807/44836554-ed1aff80-ac54-11e8-8e0d-e97828ec4b65.PNG)

9. Now create openid  client which will be used to perform Single sign on. Click on the **Clients** and choose **create** to create a new client. Enter client name and select **Save**.

![8](https://user-images.githubusercontent.com/42262807/44837269-c8c02280-ac56-11e8-8672-027a29f8abad.PNG)

10. Now configure client in following way :--
-  Now  after client is created change its access type to **confidential** .

![9](https://user-images.githubusercontent.com/42262807/44837934-90b9df00-ac58-11e8-93c9-8a8aaeb71819.PNG)

- Now enter **Valid Redirect URIs** . Ex :- https://<domain-name>/oauth/callback
Copy callback URL from plugin and then click on **SAVE**.

![10](https://user-images.githubusercontent.com/42262807/44838422-b8f60d80-ac59-11e8-9bc1-0b039232c7e9.PNG)

11. Now to get group details we need to perform its client mapping with group membership else group details will not be fetched. So in client select **Mappers** and then click on **create**.  Select mapper type **Group Membership** and enter name and token claim-name i.e the attribute name corresponding which groups will be fetched and click on **save**.

![11](https://user-images.githubusercontent.com/42262807/44839424-59e5c800-ac5c-11e8-81e2-2b5a9b2632bf.PNG)

_Note:-- If full path is on group path will be fetched else group name will be fetched._

12. Now we need to get client secret . So select **Clients** from left options and select credentials and copy your secret from here.

![12](https://user-images.githubusercontent.com/42262807/44839882-7df5d900-ac5d-11e8-847b-a6bbc6849925.PNG)

13. Enter copied Client Secret here Client ID will be your client name, scope is not required. Host name will be https://<domain-name> . Click on **Save** .

![13](https://user-images.githubusercontent.com/42262807/44841303-adf2ab80-ac60-11e8-9907-cea3067438ed.PNG)

14. Test Configuration

![14](https://user-images.githubusercontent.com/42262807/44843936-2b211f00-ac67-11e8-9d53-6866a34ac74b.PNG)

15. **Configure User Pofile Mapping** : Go to attribute mapping tab. Enter the following values,
• **Username** : Name of the any attribute from Test Configuration.
• **Email** : Name of the any attribute from Test configuration.
• **Full name attribute** : Name of the **name** attribute from Test configuration.

![15](https://user-images.githubusercontent.com/42262807/44844186-d29e5180-ac67-11e8-80e3-fc341faf3788.PNG)

Else, you an also configure by first name and last name.

• **Username** : Name of the any attribute from Test Configuration.
• **Email** : Name of the any attribute from Test configuration.
• **First name** : Name of the _givenName_ attribute from Test Configuration.
• **Last name** : Name of the _familyName_ attribute from Test Configuration.

![16](https://user-images.githubusercontent.com/42262807/44844406-7425a300-ac68-11e8-8401-435c54c581d7.PNG)

16. Group Mapping.

- **Group Attribute** : Name of the Needed attribute from the Test configuration to map groups.

You can check **Test Configuration Results** to get a better idea as to which values to map here.
Under the Group Mapping Section configure which GROUP value coming in the Test
Configuration needs to be mapped to which role. The Group value coming in the Test
Configuration will be mapped to the Role assigned here and the user will be assigned that
role.

![17](https://user-images.githubusercontent.com/42262807/44844651-20678980-ac69-11e8-9a7b-baf4e6a248ef.PNG)

17. **Domain Restriction** : Go to Sign In Settings, enter domain name which should be
allowed for login.

eg. Allowed Domain is miniorange.com then user with abc@miniorange.com can only able
to do login.

![18](https://user-images.githubusercontent.com/42262807/44844780-74726e00-ac69-11e8-8e1c-19776f5f6bce.PNG)





 






















