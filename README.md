# enrich

*Enrich your Stormpath User accounts with juicy data!*


## Purpose

If you use [Stormpath][] to store and manage your user accounts, `enrich` can be
used to easily populate additional information about your users magically.

Currently, `enrich` will set the following basic fields for your user accounts,
all based off the user's email address:

- Given Name (*first name*)
- Surname (*last name*)

`enrich` will also add data to your user's `customData` store as well, and
include the following fields inside of an `enrich` JSON object:

- `websites` - Array of websites this user is associated with.
- `demographics` - A JSON structure with the following contents:
  - `age` - The user's age as an int.
  - `location` - The user's general location as a string.
  - `gender` - The user's gender as a string (`male`, `female`, or `unknown`).
  - `ageRange` - The user's estimated age range as a string.
- `social_profiles` - The user's social profiles as an array of JSON objects.
- `organizations` - A list of organizations as an array of JSON objects.
- `digitalFootprint` - A JSON object which contains information about this
  user's digital footprint.
- `photos` - An array of JSON objects which hold this user's profile photos for
  various services.

This is useful because in many cases, it is convenient to register new user
accounts with as little information as possible (`email` and `password`), but
it's also nice to have other information on users (name, age, social profiles,
photos, etc.).

`enrich` is meant to make your user profiles powerful and standardized giving
you more power and insight over your user base.


  [Stormpath]: https://stormpath.com/ "Stormpath"
