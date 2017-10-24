# Create an App on Tradeshift

Tradeshift's platform exposes a wide array of useful end-points. To integrate your application, run through the following steps.

- Log in to [sandbox.tradeshift.com](https://sandbox.tradeshift.com). This environment is completely isolated from production. Once you're production-ready, the same steps will be repeated on our production site: [go.tradeshift.com](https://go.tradeshift.com/)

- Under apps, search for an app called **Developer**, or once logged in, you can [click this link](https://sandbox.tradeshift.com/#/apps/Tradeshift.Developer/).

- Once in the Developer app, you will be prompted to enter a VendorID. This would normally be the name of your organization. For example, Tradeshift's vendor ID is "Tradeshift".

- Click the `Create App` button in the top-right corner of the screen, which will display a form to submit your app's settings.

- Fill in all of the fields. Before you submit by clicking `Create App`, copy/paste your **oAuth2 Client Secret** into a safe place. For security reasons, we don't pull or display the client secret again after it has been submitted. So if it is lost, you will need to submit a new one (we're looking to address this pain-point in the future).

- You will likely want to find an oAuth2 library for whatever platform you're using, to avoid writing a custom implementation. The oAuth2 flow requires four parameters (other than the client secret, you can get these from the Develop app anytime):

  - **Client id:** this will be your `VenderID.AppID`. For example, the ID for our Developer app is `Tradeshift.Developer`.
  - **Client secret:** a key that should never be exposed. The authorization server uses this to confirm that the request is coming from your app, and from nowhere else.
  - **Redirect URI:** In the oAuth2 flow, your server first requests an authorization code, then the authorization server redirects to this URL.
  - **Authorization Server URL:** in the first leg of the flow, your server redirects to this URL to obtain the authorization code, which will be send to the **Redirect URI**.
    - sandbox (also used for local development): https://api-sandbox.tradeshift.com/tradeshift
    - production: https://api.tradeshift.com/tradeshift

- **Important:** to get the oAuth2 flow working on a local development machine, we must expose a public domain, so that the authorization server can redirect to the server on the local machine. Two popular services for doing this are [pagekite](https://pagekite.net/) and [ngrok](https://ngrok.com/). Pagekite is slightly cheaper (around $3/month).

- Because you'll need a separate **redirect URI** for your local development environment, versus when your app is running from your host, it's easiest to create two app entries in sandbox.

To sum it up, by the time you publish to production, you'll have **three** app entries: two in sandbox (one of them for your local setup, and one for staging), and one in production.
