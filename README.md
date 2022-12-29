## collection of jackpot code inspection / refactoring / hint files

usage:

* copy to ~/.netbeans/[version]/conf/rules
  * restart NetBeans
  * enable in tools -> options -> editor -> hints for all projects
  * or in project -> properties -> hints on a per-project basis
  * tip: changes to hint files in this folder will be automatically picked up on safe
* or run via "Run File" action when a hint file is opened or selected
* or use directly with jackpot via CLI or build process

requirements:

* a current NetBeans release or
* when used via CLI the JDK executing the task must be 17 or later [^1]

<br/>

FAQ:

Q: Can I apply suggested inspections without code review and testing?  
A: No.

Q: After applying an inspection, another inspection appeared. Why?  
A: Applying a rule can trigger another rule. It is recommended to run larger
   inspections again to account for that possiblity.

Q: Foo is not deprecated in Java X, why does a rule suggest me a refactoring?  
A: Deprecations are not backported in Java. As soon there is a migration path available,
   an inspection might suggest it anyway [^2].

Q: Shouldn't the hint files be split into individual rules so that it is easier to select which to apply?  
A: Probably :) But for now finding a rule and commenting it out seems to be a workable solution.

[^1]: might be temporary
[^2]: Example: Runtime.exec(String command) is [deprecated since JDK 18](https://github.com/openjdk/jdk/pull/6233 ), but the
 reason why it has been deprecated applies to all JDKs before 18 too. There is also a migration path available.
