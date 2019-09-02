# Conan Package Manager

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
