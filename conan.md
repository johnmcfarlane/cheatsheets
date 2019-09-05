# Conan Package Manager

## Baffling Sequence of Arbitrary Symbols

<pre>
Version:                 <b>user/repo/package:user/1.2.3:channel</b>
URL: https://bintray.com/<b>user/repo/package:user/1.2.3:channel</b>

grabber: conan remote add <REMOTE> https://api.bintray.com/conan/user/repo

recipe:                             <b>package/1.2.3@user/channel</b>
intaller:             conan install <b>package/1.2.3@user/channel</b> --build=missing
conanfile.py:    python requires = "<b>package/1.2.3@user/channel</b>"

build:   conan create . <b>user/repo</b> <your_profile_and_settings>
conan upload -r _user/_repo --all <b>package/1.2.3@user/channel</b>
</pre>

## Some Things to Try While Uploading a Package to Bintray

```bash
pip install conan
conan remote add johnmcfarlane/cnl https://api.bintray.com/conan/johnmcfarlane/cnl
conan user -p <key> -r johnmcfarlane/cnl johnmcfarlane
conan create . cnl/0.0.1@johnmcfarlane/development
conan upload cnl/0.0.1@johnmcfarlane/development -r johnmcfarlane/cnl
```

## Search for Packages

From [getting started](https://docs.conan.io/en/latest/getting_started.html#an-md5-encrypter-using-the-poco-libraries):

```sh
conan search Poco* --remote=conan-center
```
