# SE4367_MP2 (See below for MP1)

## Part One
I added the AndroidInstrument to the same package and location that I had the MP1 files in. I replaced the "Hello" value with my netid, "axc180230". Then I instrumented it using one of the following options.

### Code to run:
C:\Program Files\Java\jre1.8.0_281\bin\javaw.exe
-Dfile.encoding=UTF-8
-classpath "C:\Users\angel\eclipse-workspace\a1\lib\soot-3.3.0.jar;C:\Users\angel\eclipse-workspace\a1\bin;C:\Users\angel\eclipse-workspace\a1\lib" com.axc180230.a1.AndroidInstrument
-android-jars "C:\Users\angel\eclipse-workspace\a1\lib\android-platforms-master"
-process-dir "C:\Users\angel\eclipse-workspace\a1\lib\sq3.apk"

### In IDE (Eclipse)
Run class AndroidInstrument

### Code Output:
```
Soot started on Tue Apr 27 19:36:49 CDT 2021
[main] INFO soot.toDex.DexPrinter - Writing APK to "sootOutput\sq3.apk".
[main] INFO soot.toDex.DexPrinter - Do not forget to sign the .apk file with jarsigner and to align it with zipalign
Soot finished on Tue Apr 27 19:36:52 CDT 2021
Soot has run for 0 min. 3 sec.
```

### Generated apk File
New generated apk file in 'a1\sootOutput' with file name of 'sq3.apk'

## Part Two: Step 1 Generate Keystore
Next, I generated the  keystore. 

### Code to Run (In Command Line):
cd /c/"Program Files"/Java/jdk1.8.0_281/bin
keytool -genkey -v -keystore my.keystore -keyalg RSA -keysize 2048 -validity 10000 -alias app

### Code Output:
```
Enter keystore password:
Re-enter new password:
What is your first and last name?
  [Unknown]:  Angel Castaneda
What is the name of your organizational unit?
  [Unknown]:  SE 4367
What is the name of your organization?
  [Unknown]:  UTD
What is the name of your City or Locality?
  [Unknown]:  Dallas
What is the name of your State or Province?
  [Unknown]:  Texas
What is the two-letter country code for this unit?
  [Unknown]:  TX
Is CN=Angel Castaneda, OU=SE 4367, O=UTD, L=Dallas, ST=Texas, C=TX correct?
  [no]:  Yes

Generating 2,048 bit RSA key pair and self-signed certificate (SHA256withRSA) wi
th a validity of 10,000 days
        for: CN=Angel Castaneda, OU=SE 4367, O=UTD, L=Dallas, ST=Texas, C=TX
[Storing my.keystore]
```

## Part Two: Step 2 Zipalign
Next, I installed Android Studio and used the zipalign tool to optimze and align. The new generated apk file in 'a1\sootOutput' with file name of 'my-aligned.apk'.

### Code to Run (In Command Line):
To Zipalign:
/c/Users/angel/AppData/Local/Android/Sdk/build-tools/30.0.3/zipalign -p 4 /c/Users/angel/eclipse-workspace/a1/sootOutput/sq3.apk /c/Users/angel/eclipse-workspace/a1/sootOutput/my-aligned.apk

To Verify Zipalign
/c/Users/angel/AppData/Local/Android/Sdk/build-tools/30.0.3/zipalign -c 4 /c/Users/angel/eclipse-workspace/a1/sootOutput/my-aligned.apk

## Part Three: Step 3 Sign & Verify:
Finally, I used Jarsinger to sign and verify the new aligned apk file. 

### Code to Run (In Command Line):
cd /c/"Program Files"/Java/jdk1.8.0_281/bin
/c/"Program Files"/Java/jdk1.8.0_281/bin/jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my.keystore /c/Users/angel/eclipse-workspace/a1/sootOutput/my-aligned.apk app


### Code Output:
```
Enter Passphrase for keystore:
 updating: META-INF/MANIFEST.MF
   adding: META-INF/APP.SF
   adding: META-INF/APP.RSA
  signing: res/drawable/action_about.png
  signing: res/drawable/action_search.png
  signing: res/drawable/action_settings.png
  signing: res/drawable/content_discard.png
  signing: res/drawable/content_edit.png
  signing: res/drawable/content_email.png
  signing: res/drawable/content_new.png
  signing: res/drawable/content_remove.png
  signing: res/drawable/database.png
  signing: res/drawable/folder.png
  signing: res/layout/about.xml
  signing: res/layout/apps.xml
  signing: res/layout/bookmarks.xml
  signing: res/layout/browser.xml
  signing: res/layout/database_list.xml
  signing: res/layout/database_records.xml
  signing: res/layout/database_tables.xml
  signing: res/layout/filter.xml
  signing: res/layout/fragment_tabs_pager.xml
  signing: res/layout/list_item_app.xml
  signing: res/layout/list_item_bookmark.xml
  signing: res/layout/list_item_details.xml
  signing: res/layout/list_item_simple.xml
  signing: res/layout/recent.xml
  signing: res/layout/tab_view.xml
  signing: res/layout/table_list_item.xml
  signing: res/layout/table_record.xml
  signing: res/xml/preferences.xml
  signing: AndroidManifest.xml
  signing: resources.arsc
  signing: res/layout-v11/about.xml
  signing: res/layout-v11/filter.xml
  signing: res/layout-v11/table_record.xml
  signing: res/drawable-hdpi/action_about.png
  signing: res/drawable-hdpi/action_search.png
  signing: res/drawable-hdpi/action_settings.png
  signing: res/drawable-hdpi/content_discard.png
  signing: res/drawable-hdpi/content_edit.png
  signing: res/drawable-hdpi/content_email.png
  signing: res/drawable-hdpi/content_new.png
  signing: res/drawable-hdpi/content_remove.png
  signing: res/drawable-hdpi/database.png
  signing: res/drawable-ldpi/database.png
  signing: res/drawable-mdpi/action_about.png
  signing: res/drawable-mdpi/action_search.png
  signing: res/drawable-mdpi/action_settings.png
  signing: res/drawable-mdpi/content_discard.png
  signing: res/drawable-mdpi/content_edit.png
  signing: res/drawable-mdpi/content_email.png
  signing: res/drawable-mdpi/content_new.png
  signing: res/drawable-mdpi/content_remove.png
  signing: res/drawable-mdpi/database.png
  signing: res/drawable-xhdpi/action_about.png
  signing: res/drawable-xhdpi/action_search.png
  signing: res/drawable-xhdpi/action_settings.png
  signing: res/drawable-xhdpi/content_discard.png
  signing: res/drawable-xhdpi/content_edit.png
  signing: res/drawable-xhdpi/content_email.png
  signing: res/drawable-xhdpi/content_new.png
  signing: res/drawable-xhdpi/content_remove.png
  signing: classes.dex
>>> Signer
    X.509, CN=Angel Castaneda, OU=SE 4367, O=UTD, L=Dallas, ST=Texas, C=TX
    [trusted certificate]

jar signed.

Warning:
The signer's certificate is self-signed.
The SHA1 algorithm specified for the -digestalg option is considered a security
risk. This algorithm will be disabled in a future update.
The SHA1withRSA algorithm specified for the -sigalg option is considered a secur
ity risk. This algorithm will be disabled in a future update.
```



# SE4367_MP1

## Disclaimer
I was not able to run the java programs using the run line since Soot requires Java 8 (or earlier) and my system already had a later version of Java installed. I updated PATH and CLASSPATH variables, it still would not run from the command line. I was able to install Eclipse (I regularly use IntelliJ) and was able to have it only use Java 8 so that the programs could run. I have included the Java commands that should be able to used in order to run programs. However, if that fails the programs should still run through an IDE that uses Java 8 by cloning the git hub repository to your local drive. The code assumes the package is in the same structure as the github and start at the (repository) root directory of a1/.

Additionally, I created a package using (what I belive to be) best practices, but that forced me to update the file names refernced to include that package. This slightly alters the out put since those also include the package name.


## Part Zero
### Code to run:
javac -cp /a1/src/com/axc180230/a1 TestSoot.java
java -cp  /a1/src/com/axc180230/a1 TestSoot

### In IDE (Eclipse)
Run class TestSoot

### Code Output:
```
r0 := @this: com.axc180230.a1.HelloThread$TestThread
<com.axc180230.a1.HelloThread: int x> = 1
return
specialinvoke r0.<java.lang.Thread: void <init>()>()
return
r0 := @this: com.axc180230.a1.HelloThread
specialinvoke r0.<java.lang.Object: void <init>()>()
return
r0 := @this: com.axc180230.a1.HelloThread$TestThread
<com.axc180230.a1.HelloThread: int x> = 0
$i0 = r0.<com.axc180230.a1.HelloThread$TestThread: int y>
$i1 = $i0 + 1
r0.<com.axc180230.a1.HelloThread$TestThread: int y> = $i1
return
r0 := @parameter0: java.lang.String[]
$r2 = new com.axc180230.a1.HelloThread$TestThread
specialinvoke $r2.<com.axc180230.a1.HelloThread$TestThread: void <init>()>()
virtualinvoke $r2.<com.axc180230.a1.HelloThread$TestThread: void start()>()
$i3 = $r2.<com.axc180230.a1.HelloThread$TestThread: int y>
$i1 = <com.axc180230.a1.HelloThread: int x>
$i2 = 1 / $i1
i0 = $i3 + $i2
$r3 = <java.lang.System: java.io.PrintStream out>
virtualinvoke $r3.<java.io.PrintStream: void println(int)>(i0)
return
```


## Part One
### Code To Run
javac -cp /a1/src/com/axc180230/a1 *.java
java -cp /a1/src/com/axc180230/a1 TestDominatorFinder

### In IDE (Eclipse)
Run class TestDominatorFinder

### Code Output
```
r0 := @this: com.axc180230.a1.GCD is dominated by r0 := @this: com.axc180230.a1.GCD
specialinvoke r0.<java.lang.Object: void <init>()>() is dominated by r0 := @this: com.axc180230.a1.GCD
specialinvoke r0.<java.lang.Object: void <init>()>() is dominated by specialinvoke r0.<java.lang.Object: void <init>()>()
return is dominated by r0 := @this: com.axc180230.a1.GCD
return is dominated by specialinvoke r0.<java.lang.Object: void <init>()>()
return is dominated by return
r0 := @parameter0: java.lang.String[] is dominated by r0 := @parameter0: java.lang.String[]
$i2 = lengthof r0 is dominated by r0 := @parameter0: java.lang.String[]
$i2 = lengthof r0 is dominated by $i2 = lengthof r0
if $i2 >= 2 goto $r1 = r0[0] is dominated by r0 := @parameter0: java.lang.String[]
if $i2 >= 2 goto $r1 = r0[0] is dominated by $i2 = lengthof r0
if $i2 >= 2 goto $r1 = r0[0] is dominated by if $i2 >= 2 goto $r1 = r0[0]
$r11 = <java.lang.System: java.io.PrintStream err> is dominated by r0 := @parameter0: java.lang.String[]
$r11 = <java.lang.System: java.io.PrintStream err> is dominated by $i2 = lengthof r0
$r11 = <java.lang.System: java.io.PrintStream err> is dominated by if $i2 >= 2 goto $r1 = r0[0]
$r11 = <java.lang.System: java.io.PrintStream err> is dominated by $r11 = <java.lang.System: java.io.PrintStream err>
virtualinvoke $r11.<java.io.PrintStream: void println(java.lang.String)>("java GCD int1 int2\nExample: java GCD 876 267") is dominated by r0 := @parameter0: java.lang.String[]
virtualinvoke $r11.<java.io.PrintStream: void println(java.lang.String)>("java GCD int1 int2\nExample: java GCD 876 267") is dominated by $i2 = lengthof r0
virtualinvoke $r11.<java.io.PrintStream: void println(java.lang.String)>("java GCD int1 int2\nExample: java GCD 876 267") is dominated by if $i2 >= 2 goto $r1 = r0[0]
virtualinvoke $r11.<java.io.PrintStream: void println(java.lang.String)>("java GCD int1 int2\nExample: java GCD 876 267") is dominated by $r11 = <java.lang.System: java.io.PrintStream err>
virtualinvoke $r11.<java.io.PrintStream: void println(java.lang.String)>("java GCD int1 int2\nExample: java GCD 876 267") is dominated by virtualinvoke $r11.<java.io.PrintStream: void println(java.lang.String)>("java GCD int1 int2\nExample: java GCD 876 267")
return is dominated by r0 := @parameter0: java.lang.String[]
return is dominated by $i2 = lengthof r0
return is dominated by if $i2 >= 2 goto $r1 = r0[0]
return is dominated by $r11 = <java.lang.System: java.io.PrintStream err>
return is dominated by virtualinvoke $r11.<java.io.PrintStream: void println(java.lang.String)>("java GCD int1 int2\nExample: java GCD 876 267")
return is dominated by return
$r1 = r0[0] is dominated by r0 := @parameter0: java.lang.String[]
$r1 = r0[0] is dominated by $i2 = lengthof r0
$r1 = r0[0] is dominated by if $i2 >= 2 goto $r1 = r0[0]
$r1 = r0[0] is dominated by $r1 = r0[0]
i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1) is dominated by r0 := @parameter0: java.lang.String[]
i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1) is dominated by $i2 = lengthof r0
i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1) is dominated by if $i2 >= 2 goto $r1 = r0[0]
i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1) is dominated by $r1 = r0[0]
i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1) is dominated by i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1)
$r2 = r0[1] is dominated by r0 := @parameter0: java.lang.String[]
$r2 = r0[1] is dominated by $i2 = lengthof r0
$r2 = r0[1] is dominated by if $i2 >= 2 goto $r1 = r0[0]
$r2 = r0[1] is dominated by $r1 = r0[0]
$r2 = r0[1] is dominated by i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1)
$r2 = r0[1] is dominated by $r2 = r0[1]
i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2) is dominated by r0 := @parameter0: java.lang.String[]
i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2) is dominated by $i2 = lengthof r0
i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2) is dominated by if $i2 >= 2 goto $r1 = r0[0]
i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2) is dominated by $r1 = r0[0]
i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2) is dominated by i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1)
i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2) is dominated by $r2 = r0[1]
i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2) is dominated by i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2)
$r4 = <java.lang.System: java.io.PrintStream out> is dominated by r0 := @parameter0: java.lang.String[]
$r4 = <java.lang.System: java.io.PrintStream out> is dominated by $i2 = lengthof r0
$r4 = <java.lang.System: java.io.PrintStream out> is dominated by if $i2 >= 2 goto $r1 = r0[0]
$r4 = <java.lang.System: java.io.PrintStream out> is dominated by $r1 = r0[0]
$r4 = <java.lang.System: java.io.PrintStream out> is dominated by i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1)
$r4 = <java.lang.System: java.io.PrintStream out> is dominated by $r2 = r0[1]
$r4 = <java.lang.System: java.io.PrintStream out> is dominated by i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2)
$r4 = <java.lang.System: java.io.PrintStream out> is dominated by $r4 = <java.lang.System: java.io.PrintStream out>
$r3 = new java.lang.StringBuilder is dominated by r0 := @parameter0: java.lang.String[]
$r3 = new java.lang.StringBuilder is dominated by $i2 = lengthof r0
$r3 = new java.lang.StringBuilder is dominated by if $i2 >= 2 goto $r1 = r0[0]
$r3 = new java.lang.StringBuilder is dominated by $r1 = r0[0]
$r3 = new java.lang.StringBuilder is dominated by i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1)
$r3 = new java.lang.StringBuilder is dominated by $r2 = r0[1]
$r3 = new java.lang.StringBuilder is dominated by i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2)
$r3 = new java.lang.StringBuilder is dominated by $r4 = <java.lang.System: java.io.PrintStream out>
$r3 = new java.lang.StringBuilder is dominated by $r3 = new java.lang.StringBuilder
specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(") is dominated by r0 := @parameter0: java.lang.String[]
specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(") is dominated by $i2 = lengthof r0
specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(") is dominated by if $i2 >= 2 goto $r1 = r0[0]
specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(") is dominated by $r1 = r0[0]
specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(") is dominated by i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1)
specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(") is dominated by $r2 = r0[1]
specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(") is dominated by i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2)
specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(") is dominated by $r4 = <java.lang.System: java.io.PrintStream out>
specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(") is dominated by $r3 = new java.lang.StringBuilder
specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(") is dominated by specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(")
$r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0) is dominated by r0 := @parameter0: java.lang.String[]
$r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0) is dominated by $i2 = lengthof r0
$r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0) is dominated by if $i2 >= 2 goto $r1 = r0[0]
$r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0) is dominated by $r1 = r0[0]
$r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0) is dominated by i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1)
$r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0) is dominated by $r2 = r0[1]
$r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0) is dominated by i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2)
$r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0) is dominated by $r4 = <java.lang.System: java.io.PrintStream out>
$r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0) is dominated by $r3 = new java.lang.StringBuilder
$r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0) is dominated by specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(")
$r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0) is dominated by $r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0)
$r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ") is dominated by r0 := @parameter0: java.lang.String[]
$r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ") is dominated by $i2 = lengthof r0
$r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ") is dominated by if $i2 >= 2 goto $r1 = r0[0]
$r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ") is dominated by $r1 = r0[0]
$r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ") is dominated by i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1)
$r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ") is dominated by $r2 = r0[1]
$r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ") is dominated by i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2)
$r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ") is dominated by $r4 = <java.lang.System: java.io.PrintStream out>
$r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ") is dominated by $r3 = new java.lang.StringBuilder
$r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ") is dominated by specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(")
$r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ") is dominated by $r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0)
$r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ") is dominated by $r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ")
$r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1) is dominated by r0 := @parameter0: java.lang.String[]
$r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1) is dominated by $i2 = lengthof r0
$r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1) is dominated by if $i2 >= 2 goto $r1 = r0[0]
$r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1) is dominated by $r1 = r0[0]
$r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1) is dominated by i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1)
$r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1) is dominated by $r2 = r0[1]
$r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1) is dominated by i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2)
$r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1) is dominated by $r4 = <java.lang.System: java.io.PrintStream out>
$r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1) is dominated by $r3 = new java.lang.StringBuilder
$r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1) is dominated by specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(")
$r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1) is dominated by $r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0)
$r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1) is dominated by $r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ")
$r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1) is dominated by $r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1)
$r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ") is dominated by r0 := @parameter0: java.lang.String[]
$r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ") is dominated by $i2 = lengthof r0
$r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ") is dominated by if $i2 >= 2 goto $r1 = r0[0]
$r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ") is dominated by $r1 = r0[0]
$r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ") is dominated by i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1)
$r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ") is dominated by $r2 = r0[1]
$r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ") is dominated by i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2)
$r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ") is dominated by $r4 = <java.lang.System: java.io.PrintStream out>
$r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ") is dominated by $r3 = new java.lang.StringBuilder
$r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ") is dominated by specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(")
$r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ") is dominated by $r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0)
$r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ") is dominated by $r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ")
$r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ") is dominated by $r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1)
$r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ") is dominated by $r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ")
$i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1) is dominated by r0 := @parameter0: java.lang.String[]
$i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1) is dominated by $i2 = lengthof r0
$i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1) is dominated by if $i2 >= 2 goto $r1 = r0[0]
$i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1) is dominated by $r1 = r0[0]
$i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1) is dominated by i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1)
$i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1) is dominated by $r2 = r0[1]
$i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1) is dominated by i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2)
$i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1) is dominated by $r4 = <java.lang.System: java.io.PrintStream out>
$i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1) is dominated by $r3 = new java.lang.StringBuilder
$i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1) is dominated by specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(")
$i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1) is dominated by $r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0)
$i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1) is dominated by $r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ")
$i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1) is dominated by $r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1)
$i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1) is dominated by $r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ")
$i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1) is dominated by $i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1)
$r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3) is dominated by r0 := @parameter0: java.lang.String[]
$r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3) is dominated by $i2 = lengthof r0
$r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3) is dominated by if $i2 >= 2 goto $r1 = r0[0]
$r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3) is dominated by $r1 = r0[0]
$r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3) is dominated by i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1)
$r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3) is dominated by $r2 = r0[1]
$r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3) is dominated by i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2)
$r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3) is dominated by $r4 = <java.lang.System: java.io.PrintStream out>
$r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3) is dominated by $r3 = new java.lang.StringBuilder
$r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3) is dominated by specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(")
$r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3) is dominated by $r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0)
$r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3) is dominated by $r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ")
$r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3) is dominated by $r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1)
$r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3) is dominated by $r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ")
$r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3) is dominated by $i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1)
$r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3) is dominated by $r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3)
$r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>() is dominated by r0 := @parameter0: java.lang.String[]
$r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>() is dominated by $i2 = lengthof r0
$r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>() is dominated by if $i2 >= 2 goto $r1 = r0[0]
$r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>() is dominated by $r1 = r0[0]
$r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>() is dominated by i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1)
$r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>() is dominated by $r2 = r0[1]
$r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>() is dominated by i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2)
$r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>() is dominated by $r4 = <java.lang.System: java.io.PrintStream out>
$r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>() is dominated by $r3 = new java.lang.StringBuilder
$r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>() is dominated by specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(")
$r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>() is dominated by $r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0)
$r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>() is dominated by $r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ")
$r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>() is dominated by $r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1)
$r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>() is dominated by $r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ")
$r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>() is dominated by $i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1)
$r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>() is dominated by $r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3)
$r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>() is dominated by $r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>()
virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by r0 := @parameter0: java.lang.String[]
virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by $i2 = lengthof r0
virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by if $i2 >= 2 goto $r1 = r0[0]
virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by $r1 = r0[0]
virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1)
virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by $r2 = r0[1]
virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2)
virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by $r4 = <java.lang.System: java.io.PrintStream out>
virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by $r3 = new java.lang.StringBuilder
virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(")
virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by $r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0)
virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by $r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ")
virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by $r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1)
virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by $r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ")
virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by $i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1)
virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by $r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3)
virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by $r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>()
virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10)
return is dominated by r0 := @parameter0: java.lang.String[]
return is dominated by $i2 = lengthof r0
return is dominated by if $i2 >= 2 goto $r1 = r0[0]
return is dominated by $r1 = r0[0]
return is dominated by i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1)
return is dominated by $r2 = r0[1]
return is dominated by i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2)
return is dominated by $r4 = <java.lang.System: java.io.PrintStream out>
return is dominated by $r3 = new java.lang.StringBuilder
return is dominated by specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(")
return is dominated by $r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0)
return is dominated by $r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ")
return is dominated by $r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1)
return is dominated by $r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ")
return is dominated by $i3 = staticinvoke <com.axc180230.a1.GCD: int gcd(int,int)>(i0, i1)
return is dominated by $r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3)
return is dominated by $r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>()
return is dominated by virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10)
return is dominated by return
i0 := @parameter0: int is dominated by i0 := @parameter0: int
i1 := @parameter1: int is dominated by i0 := @parameter0: int
i1 := @parameter1: int is dominated by i1 := @parameter1: int
if i0 <= i1 goto i8 = i0 is dominated by i0 := @parameter0: int
if i0 <= i1 goto i8 = i0 is dominated by i1 := @parameter1: int
if i0 <= i1 goto i8 = i0 is dominated by if i0 <= i1 goto i8 = i0
i7 = i1 is dominated by i0 := @parameter0: int
i7 = i1 is dominated by i1 := @parameter1: int
i7 = i1 is dominated by if i0 <= i1 goto i8 = i0
i7 = i1 is dominated by i7 = i1
goto [?= (branch)] is dominated by i0 := @parameter0: int
goto [?= (branch)] is dominated by i1 := @parameter1: int
goto [?= (branch)] is dominated by if i0 <= i1 goto i8 = i0
goto [?= (branch)] is dominated by i7 = i1
goto [?= (branch)] is dominated by goto [?= (branch)]
$i5 = i0 % i7 is dominated by i0 := @parameter0: int
$i5 = i0 % i7 is dominated by i1 := @parameter1: int
$i5 = i0 % i7 is dominated by if i0 <= i1 goto i8 = i0
$i5 = i0 % i7 is dominated by i7 = i1
$i5 = i0 % i7 is dominated by goto [?= (branch)]
$i5 = i0 % i7 is dominated by $i5 = i0 % i7
$i5 = i0 % i7 is dominated by if i7 >= 1 goto $i5 = i0 % i7
if $i5 != 0 goto i7 = i7 + -1 is dominated by i0 := @parameter0: int
if $i5 != 0 goto i7 = i7 + -1 is dominated by i1 := @parameter1: int
if $i5 != 0 goto i7 = i7 + -1 is dominated by if i0 <= i1 goto i8 = i0
if $i5 != 0 goto i7 = i7 + -1 is dominated by i7 = i1
if $i5 != 0 goto i7 = i7 + -1 is dominated by goto [?= (branch)]
if $i5 != 0 goto i7 = i7 + -1 is dominated by $i5 = i0 % i7
if $i5 != 0 goto i7 = i7 + -1 is dominated by if $i5 != 0 goto i7 = i7 + -1
if $i5 != 0 goto i7 = i7 + -1 is dominated by if i7 >= 1 goto $i5 = i0 % i7
$i6 = i1 % i7 is dominated by i0 := @parameter0: int
$i6 = i1 % i7 is dominated by i1 := @parameter1: int
$i6 = i1 % i7 is dominated by if i0 <= i1 goto i8 = i0
$i6 = i1 % i7 is dominated by i7 = i1
$i6 = i1 % i7 is dominated by goto [?= (branch)]
$i6 = i1 % i7 is dominated by $i5 = i0 % i7
$i6 = i1 % i7 is dominated by if $i5 != 0 goto i7 = i7 + -1
$i6 = i1 % i7 is dominated by $i6 = i1 % i7
$i6 = i1 % i7 is dominated by if i7 >= 1 goto $i5 = i0 % i7
if $i6 != 0 goto i7 = i7 + -1 is dominated by i0 := @parameter0: int
if $i6 != 0 goto i7 = i7 + -1 is dominated by i1 := @parameter1: int
if $i6 != 0 goto i7 = i7 + -1 is dominated by if i0 <= i1 goto i8 = i0
if $i6 != 0 goto i7 = i7 + -1 is dominated by i7 = i1
if $i6 != 0 goto i7 = i7 + -1 is dominated by goto [?= (branch)]
if $i6 != 0 goto i7 = i7 + -1 is dominated by $i5 = i0 % i7
if $i6 != 0 goto i7 = i7 + -1 is dominated by if $i5 != 0 goto i7 = i7 + -1
if $i6 != 0 goto i7 = i7 + -1 is dominated by $i6 = i1 % i7
if $i6 != 0 goto i7 = i7 + -1 is dominated by if $i6 != 0 goto i7 = i7 + -1
if $i6 != 0 goto i7 = i7 + -1 is dominated by if i7 >= 1 goto $i5 = i0 % i7
return i7 is dominated by i0 := @parameter0: int
return i7 is dominated by i1 := @parameter1: int
return i7 is dominated by if i0 <= i1 goto i8 = i0
return i7 is dominated by i7 = i1
return i7 is dominated by goto [?= (branch)]
return i7 is dominated by $i5 = i0 % i7
return i7 is dominated by if $i5 != 0 goto i7 = i7 + -1
return i7 is dominated by $i6 = i1 % i7
return i7 is dominated by if $i6 != 0 goto i7 = i7 + -1
return i7 is dominated by return i7
return i7 is dominated by if i7 >= 1 goto $i5 = i0 % i7
i7 = i7 + -1 is dominated by i0 := @parameter0: int
i7 = i7 + -1 is dominated by i1 := @parameter1: int
i7 = i7 + -1 is dominated by if i0 <= i1 goto i8 = i0
i7 = i7 + -1 is dominated by i7 = i1
i7 = i7 + -1 is dominated by goto [?= (branch)]
i7 = i7 + -1 is dominated by $i5 = i0 % i7
i7 = i7 + -1 is dominated by if $i5 != 0 goto i7 = i7 + -1
i7 = i7 + -1 is dominated by i7 = i7 + -1
i7 = i7 + -1 is dominated by if i7 >= 1 goto $i5 = i0 % i7
if i7 >= 1 goto $i5 = i0 % i7 is dominated by i0 := @parameter0: int
if i7 >= 1 goto $i5 = i0 % i7 is dominated by i1 := @parameter1: int
if i7 >= 1 goto $i5 = i0 % i7 is dominated by if i0 <= i1 goto i8 = i0
if i7 >= 1 goto $i5 = i0 % i7 is dominated by i7 = i1
if i7 >= 1 goto $i5 = i0 % i7 is dominated by goto [?= (branch)]
if i7 >= 1 goto $i5 = i0 % i7 is dominated by if i7 >= 1 goto $i5 = i0 % i7
goto [?= return 1] is dominated by i0 := @parameter0: int
goto [?= return 1] is dominated by i1 := @parameter1: int
goto [?= return 1] is dominated by if i0 <= i1 goto i8 = i0
goto [?= return 1] is dominated by i7 = i1
goto [?= return 1] is dominated by goto [?= (branch)]
goto [?= return 1] is dominated by if i7 >= 1 goto $i5 = i0 % i7
goto [?= return 1] is dominated by goto [?= return 1]
i8 = i0 is dominated by i0 := @parameter0: int
i8 = i0 is dominated by i1 := @parameter1: int
i8 = i0 is dominated by if i0 <= i1 goto i8 = i0
i8 = i0 is dominated by i8 = i0
goto [?= (branch)] is dominated by i0 := @parameter0: int
goto [?= (branch)] is dominated by i1 := @parameter1: int
goto [?= (branch)] is dominated by if i0 <= i1 goto i8 = i0
goto [?= (branch)] is dominated by i8 = i0
goto [?= (branch)] is dominated by goto [?= (branch)]
$i3 = i0 % i8 is dominated by i0 := @parameter0: int
$i3 = i0 % i8 is dominated by i1 := @parameter1: int
$i3 = i0 % i8 is dominated by if i0 <= i1 goto i8 = i0
$i3 = i0 % i8 is dominated by i8 = i0
$i3 = i0 % i8 is dominated by goto [?= (branch)]
$i3 = i0 % i8 is dominated by $i3 = i0 % i8
$i3 = i0 % i8 is dominated by if i8 >= 1 goto $i3 = i0 % i8
if $i3 != 0 goto i8 = i8 + -1 is dominated by i0 := @parameter0: int
if $i3 != 0 goto i8 = i8 + -1 is dominated by i1 := @parameter1: int
if $i3 != 0 goto i8 = i8 + -1 is dominated by if i0 <= i1 goto i8 = i0
if $i3 != 0 goto i8 = i8 + -1 is dominated by i8 = i0
if $i3 != 0 goto i8 = i8 + -1 is dominated by goto [?= (branch)]
if $i3 != 0 goto i8 = i8 + -1 is dominated by $i3 = i0 % i8
if $i3 != 0 goto i8 = i8 + -1 is dominated by if $i3 != 0 goto i8 = i8 + -1
if $i3 != 0 goto i8 = i8 + -1 is dominated by if i8 >= 1 goto $i3 = i0 % i8
$i4 = i1 % i8 is dominated by i0 := @parameter0: int
$i4 = i1 % i8 is dominated by i1 := @parameter1: int
$i4 = i1 % i8 is dominated by if i0 <= i1 goto i8 = i0
$i4 = i1 % i8 is dominated by i8 = i0
$i4 = i1 % i8 is dominated by goto [?= (branch)]
$i4 = i1 % i8 is dominated by $i3 = i0 % i8
$i4 = i1 % i8 is dominated by if $i3 != 0 goto i8 = i8 + -1
$i4 = i1 % i8 is dominated by $i4 = i1 % i8
$i4 = i1 % i8 is dominated by if i8 >= 1 goto $i3 = i0 % i8
if $i4 != 0 goto i8 = i8 + -1 is dominated by i0 := @parameter0: int
if $i4 != 0 goto i8 = i8 + -1 is dominated by i1 := @parameter1: int
if $i4 != 0 goto i8 = i8 + -1 is dominated by if i0 <= i1 goto i8 = i0
if $i4 != 0 goto i8 = i8 + -1 is dominated by i8 = i0
if $i4 != 0 goto i8 = i8 + -1 is dominated by goto [?= (branch)]
if $i4 != 0 goto i8 = i8 + -1 is dominated by $i3 = i0 % i8
if $i4 != 0 goto i8 = i8 + -1 is dominated by if $i3 != 0 goto i8 = i8 + -1
if $i4 != 0 goto i8 = i8 + -1 is dominated by $i4 = i1 % i8
if $i4 != 0 goto i8 = i8 + -1 is dominated by if $i4 != 0 goto i8 = i8 + -1
if $i4 != 0 goto i8 = i8 + -1 is dominated by if i8 >= 1 goto $i3 = i0 % i8
return i8 is dominated by i0 := @parameter0: int
return i8 is dominated by i1 := @parameter1: int
return i8 is dominated by if i0 <= i1 goto i8 = i0
return i8 is dominated by i8 = i0
return i8 is dominated by goto [?= (branch)]
return i8 is dominated by $i3 = i0 % i8
return i8 is dominated by if $i3 != 0 goto i8 = i8 + -1
return i8 is dominated by $i4 = i1 % i8
return i8 is dominated by if $i4 != 0 goto i8 = i8 + -1
return i8 is dominated by return i8
return i8 is dominated by if i8 >= 1 goto $i3 = i0 % i8
i8 = i8 + -1 is dominated by i0 := @parameter0: int
i8 = i8 + -1 is dominated by i1 := @parameter1: int
i8 = i8 + -1 is dominated by if i0 <= i1 goto i8 = i0
i8 = i8 + -1 is dominated by i8 = i0
i8 = i8 + -1 is dominated by goto [?= (branch)]
i8 = i8 + -1 is dominated by $i3 = i0 % i8
i8 = i8 + -1 is dominated by if $i3 != 0 goto i8 = i8 + -1
i8 = i8 + -1 is dominated by i8 = i8 + -1
i8 = i8 + -1 is dominated by if i8 >= 1 goto $i3 = i0 % i8
if i8 >= 1 goto $i3 = i0 % i8 is dominated by i0 := @parameter0: int
if i8 >= 1 goto $i3 = i0 % i8 is dominated by i1 := @parameter1: int
if i8 >= 1 goto $i3 = i0 % i8 is dominated by if i0 <= i1 goto i8 = i0
if i8 >= 1 goto $i3 = i0 % i8 is dominated by i8 = i0
if i8 >= 1 goto $i3 = i0 % i8 is dominated by goto [?= (branch)]
if i8 >= 1 goto $i3 = i0 % i8 is dominated by if i8 >= 1 goto $i3 = i0 % i8
return 1 is dominated by i0 := @parameter0: int
return 1 is dominated by i1 := @parameter1: int
return 1 is dominated by if i0 <= i1 goto i8 = i0
return 1 is dominated by return 1
```


## Part Two

### Reading
In terms of reading, please find Spark paper and CHATransformer.java included. The Spark paper was too long for me to read fully and I will admit a lot went over my head.

### Code To Run
javac -cp /a1/src/com/axc180230/a1 *.java
java -cp /a1/src/com/axc180230/a1 TestSootCallGraph
*** The following functions have to be toggled in the code to run both call graph types
***	//enableCHACallGraph();
***	enableSparkCallGraph();
***

### In IDE (Eclipse)
Run class TestSootCallGraph
*** The following functions have to be toggled in the code to run both call graph types
***	//enableCHACallGraph();
***	enableSparkCallGraph();
***

### Code Output
#### Output with enableCHACallGraph() uncommented
 - Per Eclipse console output, ran in 2 seconds
 - Less precise than enableSparkCallGraph() since it includes more possible calls that don't actually happen in program
```
<com.axc180230.a1.Example: com.axc180230.a1.Animal selectAnimal()> may call <com.axc180230.a1.Cat: void <init>()>
<com.axc180230.a1.Example: void main(java.lang.String[])> may call <com.axc180230.a1.Example: com.axc180230.a1.Animal selectAnimal()>
<com.axc180230.a1.Example: void main(java.lang.String[])> may call <com.axc180230.a1.Fish: void saySomething()>
<com.axc180230.a1.Example: void main(java.lang.String[])> may call <com.axc180230.a1.Cat: void saySomething()>
<com.axc180230.a1.Animal: void <init>()> may call <java.lang.Object: void <init>()>
<com.axc180230.a1.Fish: void saySomething()> may call <java.lang.System: void <clinit>()>
<com.axc180230.a1.Fish: void saySomething()> may call <java.io.PrintStream: void println(java.lang.String)>
<com.axc180230.a1.Fish: void saySomething()> may call <java.lang.Object: void <clinit>()>
<com.axc180230.a1.Cat: void <init>()> may call <com.axc180230.a1.Animal: void <init>()>
<com.axc180230.a1.Cat: void saySomething()> may call <java.lang.System: void <clinit>()>
<com.axc180230.a1.Cat: void saySomething()> may call <java.io.PrintStream: void println(java.lang.String)>
<com.axc180230.a1.Cat: void saySomething()> may call <java.lang.Object: void <clinit>()>
Total Edges:12
```

#### Output with enableSparkCallGraph() uncommented
 - Per Eclipse console output, ran in 3 seconds
 - More precise than enableCHACallGraph() because the edges noted more closely align with what the Example program is actually calling.
 ```
<com.axc180230.a1.Example: com.axc180230.a1.Animal selectAnimal()> may call <com.axc180230.a1.Cat: void <init>()>
<com.axc180230.a1.Example: void main(java.lang.String[])> may call <com.axc180230.a1.Example: com.axc180230.a1.Animal selectAnimal()>
Total Edges:7
<com.axc180230.a1.Example: void main(java.lang.String[])> may call <com.axc180230.a1.Cat: void saySomething()>
<com.axc180230.a1.Animal: void <init>()> may call <java.lang.Object: void <init>()>
<com.axc180230.a1.Cat: void <init>()> may call <com.axc180230.a1.Animal: void <init>()>
<com.axc180230.a1.Cat: void saySomething()> may call <java.lang.System: void <clinit>()>
<com.axc180230.a1.Cat: void saySomething()> may call <java.lang.Object: void <clinit>()>
```


## Part Three: `Logging Method Calls`
### Code To Run
javac -cp /a1/src/com/axc180230/a1 TestSootLogging.java
java -cp /a1/src/com/axc180230/a1 TestSootLogging

### In IDE (Eclipse)
Run class TestSootLogging

### Code Output
```
r1 = staticinvoke <com.axc180230.a1.Example: com.axc180230.a1.Animal selectAnimal()>()
virtualinvoke r1.<com.axc180230.a1.Animal: void saySomething()>()
```

### Note about second task in this section
New folder called "sootOutput" created with four files 
 - com.axc180230.a1.Animal.jimple
 - com.axc180230.a1.Cat.jimple
 - com.axc180230.a1.Example.jimple
 - com.axc180230.a1.Fish.jimple
 - ** "com.axc180230.a1.Example.jimple" is the same as the original jimple code that had the two print statements inserted **

Terminal Output after running TestSootLogging.java in "Logging Method Calls" section with 'Options.v().set_output_format(1);' commented out
```
r1 = staticinvoke <com.axc180230.a1.Example: com.axc180230.a1.Animal selectAnimal()>()
virtualinvoke r1.<com.axc180230.a1.Animal: void saySomething()>()
```

Terminal Output after running "Example.java"
```
purr
```
I was not able to run "java Example" as only a class file existed and the system provided errors
 - Error: Could not find or load main class Example
 - Error: Could not find or load main class Example.class

When I tried "javap Example.class" I got.
```
Compiled from "Example.java"
public class com.axc180230.a1.Example {
  public com.axc180230.a1.Example();
  public static void main(java.lang.String[]);
  static com.axc180230.a1.Animal neverCalled();
  static com.axc180230.a1.Animal selectAnimal();
}
```


## Part Three: `Tracing Heap Access`
### Code To Run
javac -cp /a1/src/com/axc180230/a1 *.java
java -cp /a1/src/com/axc180230/a1 TestSootLoggingHeap

### In IDE (Eclipse)
Run class TestSootLoggingHeap

### Code Output
```
Thread Thread-9 wrote static field <com.axc180230.a1.HelloThread: int x>
Thread Thread-10 wrote static field <com.axc180230.a1.HelloThread: int x>
Thread Thread-10 read instance field <com.axc180230.a1.HelloThread$TestThread: int y> of object Thread[Thread-10,5,Soot Threadgroup]
Thread Thread-10 wrote instance field <com.axc180230.a1.HelloThread$TestThread: int y> of object Thread[Thread-10,5,Soot Threadgroup]
Thread Thread-9 read instance field <com.axc180230.a1.HelloThread$TestThread: int y> of object Thread[Thread-9,5,Soot Threadgroup]
Thread Thread-9 read static field <com.axc180230.a1.HelloThread: int x>
Thread Thread-9 read static field <java.lang.System: java.io.PrintStream out>
```

### Bonus
Unfortunately, I was not able to determine what value to pass as the 5th argument to Log.logFieldAcc to get it to display the value.