# PPD

To automate logging in to a website, we need to know where the `input`-elements are and how we can generate a valid a password. A Password Policy Document (PPD) is a JSON document that describes a website's password requirements and procedures for logging in, changing a password, resetting a password and registering a user. They have been proposed by Moritz Horsch [1] in his [thesis](https://tuprints.ulb.tu-darmstadt.de/7003/1/Generating%20and%20Managing%20Secure%20Passwords%20for%20Online%20Accounts.pdf), and are used in practice in the Chiff app.

## How does it work?

A PPD consists of multiple parts:

1. General information: `name`, `url`, `version` and `timestamp` describe general properties of the PPD. A PPD always has a unique ID, which is a SHA256 hash of the PPD.
2. The `characterSets` part describes whih character sets are allowed when creating a password.
3. The `properties` part describes different requirements that apply to the character sets.
4. The `service` part describes the processes for logging in, changing a password, resetting a password and registering a user.
5. The `redirect` part is mutually exclusive with `characterSets` and `service` and means is redirected to a 'main' PPD.

For a more detailed explanation of the structure of a PPD, please refer to Moritz Horsch' [thesis](https://tuprints.ulb.tu-darmstadt.de/7003/1/Generating%20and%20Managing%20Secure%20Passwords%20for%20Online%20Accounts.pdf) or check the [JSON schema](/ppd.schema.v1.1.json). In time, we will update the wiki page of this repo with more documentation.

## Contributing

Are you using Chiff and is the login or password change process not working correctly? Or are the passwords that are generated not accepted? By creating or updating a PPD in this repository, Chiff's behavior for that website will be automatically adjusted. You are very welcome to create a pull request with the changes. Please make sure the new or updated PPD is valid against the JSON-schema of the latest version.

### Chiff PPD editor

To make it easier to create, edit and test PPDs, we've created browser extension. With this extension, you get a UI to build a PPD. It can:

1. Build the password requirements and services with an UI.
2. Automatically generate redirect-PPDs for URLs.
3. Validate against the version's JSON-schema.
4. Commit and push commits to a fork of this repo and create a pull request when finished.
5. Observe mutations on websites to create `childMutationAssertions` and `attributeMutationAssertions`.

## Using PPDs

Are you the creator of a password manager or other application that could use PPDs? Feel free to use this repository as a source for your application. You can retrieve a PPD directly with via https://raw.githubusercontent.com/chiff-app/ppd/master/{version}/{id}, use a proxy in you API or mirror the repository to a CDN or your server.

## License

This repository is licensed under de Apache 2.0 license.

## References

[1] Horsch, Moritz (2018): Generating and Managing Secure Passwords for Online Accounts. Darmstadt, Technische Universität, [Ph.D. Thesis]. Retrieved from [http://tuprints.ulb.tu-darmstadt.de/view/person/Horsch=3AMoritz=3A=3A.html](http://tuprints.ulb.tu-darmstadt.de/view/person/Horsch=3AMoritz=3A=3A.html)
