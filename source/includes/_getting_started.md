# Getting Started

You need API keys and a user/password to get access to the API. To get keys, you can register at the [developer portal](http://quantiguous.com).

The API key and user/password is to be included in all API requets in a header that looks like the following:

`X-IBM-Client-Id: your-key-here`

`X-IBM-Client-Secret: your-secret-here`

`Authorization: your-user:your-password`

<aside class="notice">
You must replace <code>your-key-here</code> with your API key,  <code>your-secret-here</code> with our API secret, and <code>your-user:your-password</code> with the base64 encoded user and password.
</aside>
