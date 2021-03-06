# Apache Zookeeper bindings for fs2 


Simple, yet powerful fs2 bindings for Apache Zookeeper. 

[![Build Status](https://travis-ci.org/Spinoco/fs2-zk.svg?branch=master)](https://travis-ci.org/Spinoco/fs2-zk)
[![Gitter Chat](https://badges.gitter.im/functional-streams-for-scala/fs2.svg)](https://gitter.im/Spinoco/fs2-zk)

## Overview

Library reuses Zookeeper client, and wraps fs2 around it allowing some very simple distributed primitives.

## SBT

Add this to your sbt build file : 

```
libraryDependencies += "com.spinoco" %% "fs2-zk" % "0.4.0" 
```


### Dependencies 

Library does not have other dependencies than fs2 and zookeeper client itself: 

[Changes](CHANGES.md)

version  |    scala  |   fs2  |  zookeeper     
---------|-----------|--------|--------- 
0.4.0    | 2.11, 2.12| 1.0.0  | 3.4.10   
0.2.0    | 2.11, 2.12| 0.10.0 | 3.4.10   
0.1.6    | 2.11, 2.12| 0.9.7  | 3.4.10   

## Simple usage 

```scala 
import spinoco.fs2.zk._

// monitor all children of given node 'node1' 
// by discrete stream of changes 
client("yourZkConnectString") flatMap { zkc =>  
   clientTo(zks) flatMap { zkc => zkc.childrenOf(node1) } 
}

``` 

More examples you may found in Tests [here](https://github.com/Spinoco/fs2-zk/blob/master/src/test/scala/spinoco/fs2/zk/ZkClientSpec.scala)

