# android-sample-launchking
Learn the four kinds of launchMode of Activity. standard, singleTop, singleTask, and singleInstance. Directly learn and experience the difference of launchMode by playing the apps

please use commands to observe the task stack status below

## clear; adb shell dumpsys activity package com.holasoft.launchking

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

