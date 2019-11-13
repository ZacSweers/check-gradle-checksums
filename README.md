# check-gradle-checksums

Check your gradle-wrapper jar's checksum on CI. This is particularly useful for OSS projects.

## Prerequisites

* A Unix-like operating system: macOS, Linux, BSD. This may work on Windows, but I've not tested it.
* `sha256sum` and `curl` should be installed
* `wget` if you want to download via wget (more below)

It expects to be run from the root project directory, with 
gradle-wrapper.properties and gradle-wrapper.jar located in the 
conventional relative "gradle/wrapper" subdirectory of the root project 
directory. It expects the distribution to be "all" and not "bin".

```
- <rootProjectDir>
   - gradle
     - wrapper
       | gradle-wrapper.jar
       | gradle-wrapper.properties
```

My bash-fu isn't great and I'm sure this could be improved. PRs are also welcome to support more configuration (custom gradle-wrapper jar/properties locations, bin vs all, etc).

## Usage

The script is executed by running one of the following commands in your terminal. You can do this via the command-line with either `curl` or `wget`. The script should be run from your gradle project's root directory.

*Note: for the `sh` calls below, you may need to use `bash` directly if your CI environment's `sh` version doesn't support functions, such as on Travis-CI.* 

### via curl

```shell
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ZacSweers/check-gradle-checksums/master/check-gradle-checksums.sh)"
```

### via wget

```shell
sh -c "$(wget -O- https://raw.githubusercontent.com/ZacSweers/check-gradle-checksums/master/check-gradle-checksums.sh)"
```

### Manual inspection

It's a good idea to inspect the install script from projects you don't yet know. You can do
that by downloading the install script first, looking through it so everything looks normal,
then running it:

```shell
curl -Lo check-gradle-checksums.sh https://raw.githubusercontent.com/ZacSweers/check-gradle-checksums/master/check-gradle-checksums.sh
sh check-gradle-checksums.sh
```

### Fixed version

If you want to only use a fixed version, you can use a fixed sha in the link above. 

Example: `https://raw.githubusercontent.com/ZacSweers/check-gradle-checksums/c8dc2ae0756a8041e240cdc6fa6c38c256dfeab0/check-gradle-checksums.sh`

License
-------

    Copyright (C) 2019 Zac Sweers

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
