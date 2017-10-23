# Create an App on Tradeshift

Tradeshift's platform exposes a wide array of useful end-points. To integrate your application, run through the following steps.

- Log in to [sandbox.tradeshift.com](https://sandbox.tradeshift.com). This environment is completely isolated from production. Once you're production-ready, the same steps will be repeated on our production site: [go.tradeshift.com](https://go.tradeshift.com/)

- Under apps, search for an app called **Developer**, or once logged in, you can [click this link](https://sandbox.tradeshift.com/#/apps/Tradeshift.Developer/).

- Once in the Developer app, you will be prompted to enter a VendorID. This would normally be the name of your organization. For example, Tradeshift's vendor ID is "Tradeshift".

- click the `Create App` button in the top-right corner of the screen.

- Fill in all of the fields. Before you click `Create App`, copy/paste your your **oAuth2 Client Secret** into a safe place. For security reasons, we don't pull or display the client secret again after it has been submitted. So if you lose it, you have to submit a new one. This is a pain-point that we plan to find a work-around for in the future.

- no matter which platform you're using to build your app, there is probably an oAuth2 library you can use, to avoid writing a custom implementation. The oAuth2 flow requires four parameters (other than the client secret, you can get these from the Develop app anytime):

  - **Client id:** this will be your `VenderID.AppID`. For example, the ID for our Developer app is `Tradeshift.Developer`.
  - **Client secret:** a key that should never be exposed. The authorization server uses this to confirm that the request is coming from your app, and from nowhere else.
  - **Redirect URI:** In the oAuth2 flow, your server first requests an authorization code, then the authorization server will send the authorization code to this URL (using a redirect for added security).
  - **Authorization Server URL:** in the first leg of the flow, your app will redirect to this URL to obtain the authorization code, which will be send to the **Redirect URI**.
