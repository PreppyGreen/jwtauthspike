# JWT Auth Spike

## Create AD B2C

1. Log in to Azure Portal
2. First create a Resource Group to keep the B2C Tenant
3. Search for `Azure Active Directory B2C` - click the `Marketplace` option found
4. Click `Create new B2C Tenant`
5. Enter the details you want and click `Create`
6. Switch directory back to the subscription
7. Search again for `Azure Active Directory B2C` - click the `Marketplace` option found
8. Click `Link to existing Tenant`
9. Select your newly created B2C Tenant and Subscription and click `Create`

## AD B2C Setup

Navigate to your new Azure AD B2C and configure the following.

### Application

1. Click `Applications`
2. Click `Add`
3. Select your options and provide a Name
4. Click `Create`

### User flows (policies)

1. Click `User flows (policies)`
2. Click `New user flow`
3. Select `All`
4. Select `Sign in using ROPC`
5. Provide a Name and select the claims (include at least `Display Name` and `Identity Provider`)
6. Click `Create`

## Configuration

```
    "AzureAdB2C": {
        "Tenant": "xxxxxx.b2clogin.com",
        "TenantId": "xxxx-xxxx-xxxx-xxxx-xxxx",
        "Policy": "B2C_1_ROPC_Auth",
        "ClientId": "xxxx-xxxx-xxxx-xxxx-xxxx"
    }
```

## Build and Run API

You'll need .NET Core 3.0 installed.

Navigate to the project
```
cd src
```

And run the project
```
dotnet run
```

The example endpoint will return a 401 https://localhost:5001/weatherforecast

## Test using REST Client VSCode

Ensure you have the REST Client extention installed in VSCode

Open file test.http

Navigate to `getWeatherforecast`

Presss Ctrl+Alt+R(Cmd+Alt+R for macOS), or right-click in the editor and then select Send Request in the menu
