# android-sample-launchking
Learn the four kinds of launchMode of Activity. standard, singleTop, singleTask, and singleInstance. Directly learn and experience the difference of launchMode by playing the apps

For original documentation, please refers to [Android launchMode Documentation](http://developer.android.com/guide/topics/manifest/activity-element.html#lmode)

A stands for standard
B stands for singleTop
C stands for singleTask
D stands for singleInstance

A1 stands for standard but with different taskAffinity

please use commands to observe the task stack status below

```
clear; adb shell dumpsys activity package com.holasoft.launchking
```

There's sample below for the reference

```
ACTIVITY MANAGER ACTIVITIES (dumpsys activity activities)
  Stack #1:
    Task id #653
      TaskRecord{42f75948 #653 A=com.holasoft.launchking U=0 sz=6}
      Intent { act=android.intent.action.MAIN cat=[android.intent.category.LAUNCHER] flg=0x10200000 cmp=com.holasoft.launchking/.A }
        Hist #5: ActivityRecord{435d55d8 u0 com.holasoft.launchking/.A t653}
          Intent { cmp=com.holasoft.launchking/.A }
          ProcessRecord{43e578e8 32258:com.holasoft.launchking/u0a434}
        Hist #4: ActivityRecord{43374ea0 u0 com.holasoft.launchking/.C t653}
          Intent { cmp=com.holasoft.launchking/.C }
          ProcessRecord{43e578e8 32258:com.holasoft.launchking/u0a434}
        Hist #3: ActivityRecord{42f5e740 u0 com.holasoft.launchking/.B t653}
          Intent { cmp=com.holasoft.launchking/.B }
          ProcessRecord{43e578e8 32258:com.holasoft.launchking/u0a434}
        Hist #2: ActivityRecord{44257470 u0 com.holasoft.launchking/.A t653}
          Intent { cmp=com.holasoft.launchking/.A }
          ProcessRecord{43e578e8 32258:com.holasoft.launchking/u0a434}
        Hist #1: ActivityRecord{43af5ac8 u0 com.holasoft.launchking/.A t653}
          Intent { cmp=com.holasoft.launchking/.A }
          ProcessRecord{43e578e8 32258:com.holasoft.launchking/u0a434}
        Hist #0: ActivityRecord{43aa1058 u0 com.holasoft.launchking/.A t653}
          Intent { act=android.intent.action.MAIN cat=[android.intent.category.LAUNCHER] flg=0x10200000 cmp=com.holasoft.launchking/.A bnds=[317,978][509,1170] }
          ProcessRecord{43e578e8 32258:com.holasoft.launchking/u0a434}
    Task id #650
      TaskRecord{44181798 #650 A=.A1 U=0 sz=2}
      Intent { act=android.intent.action.MAIN cat=[android.intent.category.LAUNCHER] flg=0x10200000 cmp=com.holasoft.launchking/.A1 }
        Hist #1: ActivityRecord{441fb650 u0 com.holasoft.launchking/.A1 t650}
          Intent { cmp=com.holasoft.launchking/.A1 }
          ProcessRecord{43e578e8 32258:com.holasoft.launchking/u0a434}
        Hist #0: ActivityRecord{441d2ab8 u0 com.holasoft.launchking/.A1 t650}
          Intent { act=android.intent.action.MAIN cat=[android.intent.category.LAUNCHER] flg=0x10200000 cmp=com.holasoft.launchking/.A1 bnds=[571,978][763,1170] }
          ProcessRecord{43e578e8 32258:com.holasoft.launchking/u0a434}
```

Quick Summary for the four launchMode


* standard
	multiple instance

* singleTop
	pretty much the same to standard, but the activity would be reused if it's on the top of task. (but also receive a onNewIntent)

* singleTask
	Single instance but allow different activities within the same task stack.
	If the same activity intent triggered which the same activity created below, the activity will levearge to the top and clear up all activities above.
	For example, let C stands for singleTask
```
	before --> A C B A B

	another intent C invoked

	after --> A C

	the activities are clear above C. Only one instance of C would exist

```

* singleInstnace
	Single instance and the only activity in the task.
	For example, let D stands for singleInstance

```
	before --> [Task #1]	A C B

	intent D invoked

	then -->

		[Task #2] D

		[Task #1] A C B

	intent A invoked

	then --> 

		[Task #1] A C B A

		[Task #2] D

	because A, B, C have the same taskAffinity (default), so all will be in the same task stack

	intent C invoked (C stands for singleTask)

	then --> 

		[Task #1] A C

		[Task #2] D

	clear activities above C because it's singleTask
```

The summary description from original android documentation.
![Alt launchMode](/doc/launchMode.png?raw=true "Android launchMode")


