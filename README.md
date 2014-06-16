# stormpath-enrich

*Enrich your Stormpath User accounts, instantly!*


![Bonsai Sketch][]


## Purpose

If you use [Stormpath][] to store and manage your user accounts,
`stormpath-enrich` can be used to easily populate additional information about
your users magically.

Currently, `stormpath-enrich` will set the following basic fields for your user
accounts, all based off the user's email address:

- Given Name (*first name*)
- Surname (*last name*)

`stormpath-enrich` will also add data to your user's `customData` store.
Depending on what information is available for each user, you can have the
following `customData` fields automatically populated for you:

- photos (*a list of user photos from various services*)
- contactInfo (*this user's contact information*)
- organizations (*organizations and companies this user is a member of*)
- demographics (*demographic data about this user*)
- socialProfiles (*all of this user's social network profiles*)

Here's an example of these fields, as you can see below -- there is a lot of
information!

**photos**
```json
{
    "photos": {
        "twitter": [
            {
                "url": "https://d2ojpxxtu63wzl.cloudfront.net/static/ecf57683e2c22abb296f822377597290_fe346265298c3d008a4af9c54483809f55508dd4c238789dc9a115ae8395c381",
                "typeName": "Twitter",
                "isPrimary": false
            }
        ],
        "facebook": [
            {
                "url": "https://d2ojpxxtu63wzl.cloudfront.net/static/cf9e151530e386f6d86450206fd1345a_ea1f4c9ffb6856596b3df04b6b797de722f79a9781ba29bf172c52136f576557",
                "typeName": "Facebook",
                "isPrimary": true
            }
        ],
        "quora": [
            {
                "url": "https://d2ojpxxtu63wzl.cloudfront.net/image/8aeb64288905cbc9e73678eab24032d4_260589322c246c2e8aef934f234b4fc0c33a437e247dc80f6f9b909d2a2ba990",
                "typeName": "Quora"
            }
        ],
        "foursquare": [
            {
                "url": "https://d2ojpxxtu63wzl.cloudfront.net/static/ac4cac11df61b43c503d4c3101604742_80a63ae50b5cc0e8f9dacb522547d923f1b3961ca666fd661fb2b3f5656a644d",
                "typeName": "Foursquare",
                "isPrimary": false
            }
        ],
        "googleplus": [
            {
                "url": "https://d2ojpxxtu63wzl.cloudfront.net/static/a508fc51b2d287175f36a44aead7438a_6be07253a0bbaf5929d148cc2fca7f266ffd41a1053862e2f3016594a134602d",
                "typeName": "Google Plus",
                "isPrimary": false
            }
        ]
    }
}
```

**contactInfo**
```json
"contactInfo": {
    "familyName": "Lorang",
    "givenName": "Bart",
    "fullName": "Bart Lorang",
    "websites": [
        {
            "url": "http://fullcontact.com"
        },
        {
            "url": "http://www.flickr.com/people/39267654@N00/"
        },
        {
            "url": "http://picasaweb.google.com/lorangb"
        }
    ],
    "chats": {
        "gtalk": [
            {
                "handle": "lorangb@gmail.com"
            }
        ],
        "skype": [
            {
                "handle": "bart.lorang"
            }
        ]
    }
},
```

**organizations**
```json
"organizations": [
    {
        "name": "FullContact",
        "title": "Co-Founder & CEO",
        "isPrimary": true
    }
],
```

**demographics**
```json
"demographics": {
    "age": "33",
    "locationGeneral": "Boulder, Colorado",
    "gender": "Male",
    "ageRange": "25-34"
},
```

**socialProfiles**
```json
"socialProfiles": {
    "aboutme": [
        {
            "typeName": "About.me",
            "username": "lorangb",
            "url": "http://about.me/lorangb"
        }
    ],
    "twitter": [
        {
            "typeName": "Twitter",
            "username": "bartlorang",
            "url": "http://twitter.com/bartlorang"
        }
    ],
    "quora": [
        {
            "typeName": "Quora",
            "username": "bart-lorang",
            "url": "http://quora.com/bart-lorang"
        }
    ],
    "linkedin": [
        {
            "typeName": "LinkedIn",
            "username": "bartlorang",
            "url": "http://linkedin.com/in/bartlorang"
        }
    ],
    "facebook": [
        {
            "typeName": "Facebook",
            "username": "bartlorang",
            "url": "http://facebook.com/bartlorang"
        }
    ],
    "klout": [
        {
            "typeName": "Klout",
            "username": "lorangb",
            "url": "http://klout.com/#/lorangb"
        }
    ],
    "youtube": [
        {
            "typeName": "YouTube",
            "username": "lorangb",
            "url": "http://youtube.com/user/lorangb"
        }
    ],
    "myspace": [
        {
            "typeName": "MySpace",
            "userid": "137200880",
            "url": "http://myspace.com/137200880"
        }
    ],
    "foursquare": [
        {
            "typeName": "FourSquare",
            "username": "bartlorang",
            "url": "http://foursquare.com/bartlorang"
        }
    ],
    "googleprofile": [
        {
            "typeName": "Google Profile",
            "userid": "114426306375480734745",
            "url": "http://profiles.google.com/114426306375480734745"
        }
    ],
    "googleplus": [
        {
            "typeName": "Google Plus",
            "userid": "114426306375480734745",
            "url": "http://plus.google.com/114426306375480734745"
        }
    ]
},
```

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


  [Bonsai Sketch]: https://github.com/rdegges/stormpath-enrich/raw/master/assets/bonsai-sketch.jpg "Bonsai Sketch"
  [Stormpath]: https://stormpath.com/ "Stormpath"
  [FullContact]: http://www.fullcontact.com/ "FullContact"
  [here]: https://api.stormpath.com/register "Create a Stormpath Account"
  [over here]: https://www.fullcontact.com/developer/try-fullcontact/ "Create a FullContact Developer Account"
