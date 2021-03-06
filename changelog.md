#v2.0.0-beta5

 - Renamed a whole bunch of interface methods to simplify them. For example, `GroupInterface::getGroupPermissions()` is now `GroupInterface::getPermissions()`. Eloquent changes have occured which have allowed a clean implementation of this.
 - Adding configuration to specify default hasher for Sentry out of "native", "bcrypt" or "sha256".
 - Some older versions of PHP 5.3 (< 5.3.7) are most likely to be incompatible with the Native Hasher. Added Exception and suggestions for when this occurs. See [here](https://github.com/ircmaxell/password_compat/issues/10) and [here](https://github.com/cartalyst/sentry/issues/98#issuecomment-12974603).

#v2.0.0-beta4

 - Fixing security issue with latest persist code changes.
 - Added new column to users table, `persist_hash` (schema identical to `reset_hash`) - need to re-run migrations or modify table manually.

#v2.0.0-beta3

 - Added configuration for Laravel 4 users.
 - Added native Facade to reduce boilerplate for users outside a framework.
 - Switching from full hashing to an MD5 hash when creating a login hash (persist code) - speed improvement.
 - Allow you to override User / Group / Throttle models at runtime - `Sentry::getGroupProvider()->setModel('MyCustomModel')`.
 - User methods `addGroup()` and `removeGroup()` now return a boolean.

#v2.0.0-beta2

 - Validate that the login and password attributes are provided when authenticating and throwing dedicated exceptions for these errors.
 - `UserInterface::checkResetPassword()` renamed to `UserInterface::checkResetPasswordCode()`.
 - Adding method to return all groups - `GroupProvider::findAll()`.
 - No longer storing serialized user object in cookie / session, creating a hash based on some of the user's attributes.
 - Switch to native PHP5.5+ hasher (with forwards compatibility for PHP 5.3+) for hashing as to reduce issues moving forward
