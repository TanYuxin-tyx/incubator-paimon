<!--
Licensed to the Apache Software Foundation (ASF) under one
or more contributor license agreements.  See the NOTICE file
distributed with this work for additional information
regarding copyright ownership.  The ASF licenses this file
to you under the Apache License, Version 2.0 (the
"License"); you may not use this file except in compliance
with the License.  You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing,
software distributed under the License is distributed on an
"AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
KIND, either express or implied.  See the License for the
specific language governing permissions and limitations
under the License.
-->

# Documentation generators

This module contains generators that create HTML files directly from Flink Table Store's source code.

## Configuration documentation

The `ConfigOptionsDocGenerator` can be used to generate a reference of `ConfigOptions`. By default, a separate file is generated for each `*Options` class found in `org.apache.paimon`, `org.apache.paimon.connector` and `org.apache.paimon.connector.kafka`. 
The `@ConfigGroups` annotation can be used to generate multiple files from a single class.

To integrate an `*Options` class from another package, add another module-package argument pair to `ConfigOptionsDocGenerator#LOCATIONS`.

The files can be generated by running `mvn package -Pgenerate-docs -pl paimon-docs -nsu -DskipTests`, and can be integrated into the documentation using `{{ include generated/<file-name> >}}`.

The documentation must be regenerated whenever
* an `*Options` class was added or removed
* a `ConfigOption` was added to or removed from an `*Options` class
* a `ConfigOption` was modified in any way.