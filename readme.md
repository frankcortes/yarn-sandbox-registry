# Sandbox for yarn registry

This repo is purely for educational reasons.

This is an example of a yarn project (`test_project` folder) that uses an offline mirror (`offline_mirror` folder).
To check how the example works, follow the next steps:
```bash
# do this offline
cd test_project
yarn install
# depedencies of the project will be downloaded in a node_modules folder
# ...with internet connection should work exactly the same.
```

Use your own local dependencies

The next proccess is not totally needed, since you can do yarn add:file protocol.
Nevertheless, it could be interesting if you could keep the local dependencies
in the same way that you are saving the offline mirror. To do this:

+ rename the root folder of your package to "package"
+ compress the folder version to [nameofyourlibrary]-[version].tgz
+ move this file to the offline_mirror folder
+ executes `yarn add file`

```bash
mv [mypackage] package
tar -zcvf myownpackage-0.0.1.tgz package
mv myownpackage-0.0.1.tgz ./offline_mirror #[offline_mirror directory]
cd test_project # [project directory, in this case test_project]
yarn add file::../offline_mirror #[offline_mirror directory]
yarn install # this should work even in offline mode
```
