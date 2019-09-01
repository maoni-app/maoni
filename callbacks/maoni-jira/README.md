[![Bintray](https://img.shields.io/bintray/v/rm3l/maven/org.rm3l:maoni-jira.svg)](https://bintray.com/rm3l/maven/org.rm3l%3Amaoni-jira) 
[![Travis branch](https://img.shields.io/travis/maoni-app/maoni-jira/master.svg)](https://travis-ci.org/maoni-app/maoni-jira) 
[![Coverage Status](https://coveralls.io/repos/github/maoni-app/maoni-jira/badge.svg?branch=master)](https://coveralls.io/github/maoni-app/maoni-jira?branch=master)  
[![License](https://img.shields.io/badge/license-MIT-green.svg?style=flat)](https://github.com/rm3l/maoni-jira/blob/master/LICENSE) 

[![GitHub watchers](https://img.shields.io/github/watchers/maoni-app/maoni-jira.svg?style=social&label=Watch)](https://github.com/rm3l/maoni-jira) 
[![GitHub stars](https://img.shields.io/github/stars/maoni-app/maoni-jira.svg?style=social&label=Star)](https://github.com/rm3l/maoni-jira) 
[![GitHub forks](https://img.shields.io/github/forks/maoni-app/maoni-jira.svg?style=social&label=Fork)](https://github.com/rm3l/maoni-jira)

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Getting started](#getting-started)
- [Contribute and Improve maoni-jira!](#contribute-and-improve-maoni-jira)
  - [Publishing a new release](#publishing-a-new-release)
- [Developed by](#developed-by)
- [Credits](#credits)
- [License](#license)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

[**Maoni**](http://maoni.rm3l.org) is a lightweight open-source library for integrating 
a way to collect user feedbacks from within Android applications.

Maoni takes care of collecting user feedback using a beautiful and customizable activity. 
And anyone can provide callbacks that will perform the appropriate actions with the feedback collected.

**maoni-jira** is an example of such callback for Maoni. 
It aims at sending the valuable feedback of your app users to the specified JIRA host (as a JIRA issue).


## Getting started

Please include Maoni dependency first, by reading the instructions provided [here](http://maoni.rm3l.org).

Then grab `maoni-jira` via Gradle, by adding this to your `build.gradle`:

```gradle
  dependencies {
    // ...
    //As this will be plugged as a callback for Maoni, it requires Maoni dependency as well.
    //See http://maoni.rm3l.org for more details.
    //compile ('org.rm3l:maoni:<appropriate_version>@aar') {
    //   transitive = true;
    //}
    compile 'org.rm3l:maoni-jira:2.5.0-maoni_6.0.0'
  }
```

And set it as the listener for your Maoni instance:
```java
    //Customize the maoni-jira listener, with things like the JIRA Host REST API Base URL and the credentials to use to connect
    final org.rm3l.maoni.github.MaoniJiraListener listenerForMaoni = 
            new org.rm3l.maoni.github.MaoniJiraListener(...);
    
    new Maoni.Builder(MY_FILE_PROVIDER_AUTHORITY)
        .withListener(listenerForMaoni) //Callback from maoni-jira
        //...
        .build()
        .start(MaoniSampleMainActivity.this); //The screenshot captured is relative to this calling context 
```

**You're good to go!** Maoni will take care of validating / collecting your users' feedbacks 
and call maoni-jira as needed. 


## Contribute and Improve maoni-jira!

Contributions and issue reporting are more than welcome. 
So to help out, do feel free to fork this repo and open up a pull request. 
I'll review and merge your changes as quickly as possible.

You can use [GitHub issues](https://github.com/rm3l/maoni-jira/issues) to report bugs. 
However, please make sure your description is clear enough and has sufficient instructions 
to be able to reproduce the issue.

### Publishing a new release

All releases (Git tags) are published to [Bintray](https://bintray.com/rm3l/maven/org.rm3l%3Amaoni-jira).

To publish to Bintray, you need to have the appropriate rights. 
Additionally, your Bintray credentials are expected to be put on your local machine 
in `${HOME}/.droid/maoni.bintray.properties`, which should at least contain 
the following properties:
- `user` : the username used for publishing
- `key` : your Bintray API Key, which you can retrieve from your Bintray account

The following command can then be run to publish a new version:

```bash
./gradlew build javadoc bintrayUpload
```

## Developed by

* Armel Soro
  * [keybase.io/rm3l](https://keybase.io/rm3l)
  * [rm3l.org](https://rm3l.org) - &lt;apps+maoni-jira@rm3l.org&gt; - [@rm3l](https://twitter.com/rm3l)
  * [paypal.me/rm3l](https://paypal.me/rm3l)
  * [coinbase.com/rm3l](https://www.coinbase.com/rm3l)

## Credits

This is written in the excellent [Kotlin](https://kotlinlang.org/) programming language, and leverages some other excellent Open-Source libraries:
* [Anko](https://github.com/Kotlin/anko), by Kotlin
* [khttp](http://khttp.readthedocs.io/en/latest/#), by [jkcclemens](https://github.com/jkcclemens)

## License

    The MIT License (MIT)
    
    Copyright (c) 2017 Armel Soro
    
    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:
    
    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.
    
    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.
