Add Microsoft Azure Active Directory as an identity provider 
=============================================================

Use `Microsoft Azure Active Directory (AD) <https://azure.microsoft.com/en-us/products/active-directory/>`_ to give your organization users single sign-on (SSO) access to Aiven. 


Prerequisite steps in Aiven Console
------------------------------------

Add Azure as an :ref:`identity provider <add-idp-aiven-console>` in the Console. 


.. _configure-saml-azure:

Configure SAML on Microsoft Azure
----------------------------------

First, you set up the application on Azure. Then, you add a claim and users.


Set up an Azure application
""""""""""""""""""""""""""""

1. Log in to `Microsoft Azure <https://portal.azure.com/>`_.

2. Got to **Enterprise applications**.

3. Select **All applications**.

4. Click **New application**.

5. Select the **Add from the gallery** search bar and use the **Azure AD SAML Toolkit**.

6. Click **Add**.

7. Go back to the **Enterprise applications** list.

   .. note::

    The newly created application might not be visible yet. You can use the **All applications** filter to see the new application.  
    
8. Click on the name of the new application. The configuration opens.

9. Select **Single sign-on** configuration.

10. Select **SAML** as the single sign-on method.

11. Add the following parameters to the **Basic SAML Configuration**:

.. list-table::
      :header-rows: 1
      :align: left

      * - Parameter
        - Value
      * - ``Identifier (Entity ID)``
        - ``https://api.aiven.io/v1/sso/saml/account/{account_id}/method/{account_authentication_method_id}/metadata``
      * - ``Reply URL (Assertion Consumer Service URL)``
        - ``https://api.aiven.io/v1/sso/saml/account/{account_id}/method/{account_authentication_method_id}/acs``
      * - ``Sign on URL``
        - ``https://console.aiven.io``


12. Click **Save**.

Create a claim and add users
""""""""""""""""""""""""""""

1. In the **User Attributes & Claims**, click **Add a new claim**.

2. Create an attribute with the following data:

.. list-table::
      :header-rows: 1
      :align: left

      * - Parameter
        - Value
      * - ``Name``
        - ``email``
      * - ``Source``
        - ``Attribute``
      * - ``Source Attribute``
        - ``user.mail``

3. Download the **Certificate (Base64)** from the **SAML Signing Certificate** section.

4. Go to **Users and groups** and click **Add user**. 

5. Select the users that you want to use Azure AD to log in to Aiven. 

6. Click **Assign**.


Finish the configuration in Aiven
----------------------------------

Go back to the Aiven Console to :ref:`configure the IdP <configure-idp-aiven-console>` and complete the setup.


Troubleshooting
---------------

If you get an error message suggesting you contact your administrator, try these steps: 

#. Go to the Microsoft Azure AD user profile for the users.

#. In **Contact Info**, check whether the **Email** field is blank.

If it is blank, there are two possible solutions:

* In **User Principal Name**, if the **Identity** field is an email address, try changing the **User Attributes & Claims** to ``email = user.userprincipalname``. 

* In **Contact Info**, if none of the **Alternate email** fields are blank, try changing the **User Attributes & Claims** to ``email = user.othermail``. 

If you still have login issues, you can use the `SAML Tracer browser extension <https://addons.mozilla.org/firefox/addon/saml-tracer/>`_ to check the process step by step. If this doesn't work, get in touch with our support team at support@Aiven.io.
