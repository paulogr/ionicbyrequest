---
layout: post
title: Make your Ionic Framework app unique on App Stores
tagline: Hey, take a look at my post on AirPair about how to correctly create and change your application id when working with Ionic Framework.
category: blog
---

## Introduction

Max Lynch tweet this at the beginning of the year:

<blockquote class="twitter-tweet" lang="en"><p>A search for &quot;com.ionicframework&quot; in the Google Play store shows over 23,000 Ionic apps that didn&#39;t change the id! <a href="http://t.co/ukM50wFHbv">http://t.co/ukM50wFHbv</a></p>&mdash; Max Lynch (@maxlynch) <a href="https://twitter.com/maxlynch/status/553289730532851713">January 8, 2015</a></blockquote>

The number decrease since this tweet but still have +12k apps with default id.

Here I will describe how to create you app with a unique id or change the id of your exinting apps.

## Background Information

Both platforms, iOS and Android, uses the id to identify your app as unique on user's device and also unique in app stores. App services like Game Center or Google Play Services are linked with your app thru the id.

And as shown in Max Lynch tweet you can even find out an app on Play Store by their id. 

**You can't change your id after your app has been published at stores, doing so would cause your app to be treated as a brand new app, and existing users of your app will not see the newly packaged app as an update.**

## How to compose your App id

The id uses reverse-DNS format, initially used to describe elements of the Java class hierarchy both platforms adopt it as rule.

As general rule, if you have a website, for instance www.ionicbyrequest.com you should use as id:

```
com.ionicbyrequest.<appname>
```

## Creating an Ionic App

The best way to do it is when you're creating a new app. The Ionic CLI supports two options to do that the right way:

```bash
$ ionic start MyNewApp blank --appname MyNewApp --id com.ionicbyrequest.mynewapp
```

Simple, no ? Now when you deploy to stores your id will be unique.

## Changing an existing App

Unfortunately, the CLI has no option to change the id or app name of existing apps, you have to change it with your own hands.

Inside your project folder you'll find out the config.xml file that looks like below

```html
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<widget id="com.ionicbyrequest.mynewapp" version="0.0.1" xmlns="http://www.w3.org/ns/widgets" xmlns:cdv="http://cordova.apache.org/ns/1.0">
  <name>MyNewApp</name>
  <description>
        An Ionic Framework and Cordova project.
    </description>
  <author email="hi@ionicframework" href="http://ionicframework.com/">
      Ionic Framework Team
    </author>
  <content src="index.html"/>
  <access origin="*"/>
  <preference name="webviewbounce" value="false"/>
  <preference name="UIWebViewBounce" value="false"/>
  <preference name="DisallowOverscroll" value="true"/>
  <preference name="BackupWebStorage" value="none"/>
  <feature name="StatusBar">
    <param name="ios-package" value="CDVStatusBar" onload="true"/>
  </feature>
</widget>
```

You have to change the id attribute of widget tag to change your app id and changing the name tag for the app name.

But remember, changing your id after publish your app on stores can cause headaches as mentioned at beginning of this post.

Hope it helps and thanks for reading !

This post was publish on <a target="_blank" href="https://www.airpair.com/posts/review/552420e317321011003ddc33">@AirPair</a> too.