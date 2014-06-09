# stormpath-enrich

*Enrich your Stormpath User accounts, instantly!*


## Purpose

If you use [Stormpath][] to store and manage your user accounts,
`stormpath-enrich` can be used to easily populate additional information about
your users magically.

Currently, `stormpath-enrich` will set the following basic fields for your user
accounts, all based off the user's email address:

- Given Name (*first name*)
- Surname (*last name*)

`stormpath-enrich` will also add data to your user's `customData` store as
well, and include the following fields inside of an `stormpath-enrich` JSON
object:

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

`stormpath-enrich` is meant to make your user profiles powerful and
standardized giving you more power and insight over your user base.


# Install

You can install `stormpath-enrich` through [npm][https://www.npmjs.org/] by
running:

```console
$ npm install -g stormpath-enrich
```

**NOTE**: Depending on how you have `npm` installed, you might need to run the
above command with `sudo`.


## Setup

Once you have `stormpath-enrich` installed, you can configure it by running:

```console
$ stormpath-enrich --configure
```

This will prompt you for your [Stormpath][] and [FullContact][] API keys (which
are both required).

Don't have a Stormpath or FullContact account yet?

- Create your [Stormpath][] account [here][].
- Create your [FullContact][] account [over here][] (*note: you need a
  FullContact developer account*).


## Usage

Using `stormpath-enrich` is easy!  If you'd like to automatically enrich *all*
accounts, you can easily do so by running:

```console
$ stormpath-enrich
```

This might take a while, depending on how many user accounts you have.

If you'd like to see the available help options, you can run:

```console
$ stormpath-enrich --help
```

**NOTE**: For best results, consider running `stormpath-enrich` on a cron job --
this way, any user accounts you have will be automatically updated with the
latest information possible, and you'll continuously have an up-to-date
directory of users!


  [Stormpath]: https://stormpath.com/ "Stormpath"
  [FullContact]: http://www.fullcontact.com/ "FullContact"
  [here]: https://api.stormpath.com/register "Create a Stormpath Account"
  [over here]: https://www.fullcontact.com/developer/try-fullcontact/ "Create a FullContact Developer Account"
