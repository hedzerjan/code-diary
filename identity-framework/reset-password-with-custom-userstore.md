# Implementing a password reset with a custom user store

The usermanager needs to implement a couple of interfaces:
* IEmailStore: to send mail messages with links.
* IUserSecurityStampStore: to update the securitystamp after changing the password.

Furthermore, somehow the default tokenproviders didn't work so I added one specifically:
```csharp
options.Tokens.PasswordResetTokenProvider = TokenOptions.DefaultEmailProvider;
```

And finally I changed the allowed characters in a username, MS by default doesn't allow for spaces in the username:
```csharp
options.User.AllowedUserNameCharacters = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789-._@+ ";
```