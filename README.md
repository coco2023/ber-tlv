# [reply from ChatGtp](https://chatgpt.com/share/69b28778-191c-8012-88cf-ca98108ddd20)

## 背景：
主播最近工作遇到了使用ber-tlv的格式送值问题。但是发现卡组文档的对于用ber-tlv格式送值要求更多变，使用chatgpt生成ber-tlv方法已经不能正确送值。故前来学习本仓库用法。
</br>
再加上滞主播今天因为基础问题被工友狠狠嘲笑。于是决定痛定思痛顺便巴拉下源码，自行在本地debug，看看能不能顺利组装参数。

--- 

[![maven](https://maven-badges.herokuapp.com/maven-central/com.payneteasy/ber-tlv/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.payneteasy/ber-tlv)
[![Build Status](https://travis-ci.org/evsinev/ber-tlv.svg?branch=master)](https://travis-ci.org/evsinev/ber-tlv)
[![CircleCI](https://circleci.com/gh/evsinev/ber-tlv.svg?style=svg)](https://circleci.com/gh/evsinev/ber-tlv)

BER-TLV parser and builder
==========================

BerTlv is a java library for parsing and building BER TLV encoded data.

## Features

* supported types: amount, date, time, text, BCD, bytes
* thread safe (provides immutable container BerTlv)
* production ready (uses in several projects)
* lightweight (no external dependencies)

## Setup with dependency managers

### Maven

```xml
<dependency>
  <groupId>com.payneteasy</groupId>
  <artifactId>ber-tlv</artifactId>
  <version>1.0-11</version>
</dependency>
```

### Gradle

```groovy
implementation 'com.payneteasy:ber-tlv:1.0-11'
```

How to parse
------------

```java
byte[] bytes = HexUtil.parseHex("50045649534157131000023100000033D44122011003400000481F");

BerTlvParser parser = new BerTlvParser(LOG);
BerTlvs tlvs = parser.parse(bytes, 0, bytes.length);
  
BerTlvLogger.log("    ", tlvs, LOG);
```

How to build
------------

```java
byte[] bytes =  new BerTlvBuilder()
                .addHex(new BerTag(0x50), "56495341")
                .addHex(new BerTag(0x57), "1000023100000033D44122011003400000481F")
                .buildArray();
```


## License

The BerTlv framework is licensed under the Apache License 2.0
