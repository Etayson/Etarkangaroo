# Etarkangaroo (windows only)
Gpu math is mostly based on JeanLucPons code https://github.com/JeanLucPons/Kangaroo/blob/master/GPU/GPUMath.h<br/>
But with some additions and modifications.<br/>
Supported GPU architecture >=SM75<br/>
Futures: <br/>
Range limited to 192bit<br/>
Initial kangaroos generation happens on GPU which is slightly faster.<br/>
You can save kangaroos after certain time interval and with saving hashtable you can be sure that after restart program you will continue your job.<br/>
It is possible to reset and save the hashtable after a certain time interval, followed by automatic merging into a single hashtable.<br/>
During the merging, you possible to find the desired key, and also the merger fixes the dead kangaroos and signals the GPU to reset them.<br/>
So you not need to keep all hashtable in RAM.<br/>
Saving kangaroos, merging does not impact speed hashing.<br/>
Only saving hashtable impact speed.<br/>
Good -grid params:  
- for GTX 1660super 88,128 with PL60% speed 890Mkey/s  
- for RTX 3070 92,256 with PL56% speed 1535Mkey/s  
Usage:<br/>
```
-wmerge    automaticly merge current ht work with main ht (works together with -wsplit)
-wsplit    reset hashtable
-o         output file where the key will be saved
-wm        merge 2 source HT files to target file
-dp        number of trailing zeros distinguished point
-d         select GPU IDs (coma separated)
-pub       set single uncompressed/compressed pubkey for searching
-grid      GPUs gridsize (coma separated)
-rb        range start from
-re        end range
-kf        kangaroos work file for saving and loading
-wf        ht working file for saving
-wi        timer interval for autosaving ht/kangaroos
Example:
Etarkangaroo -dp 16 -d 0 -grid 44,64 -wf htwork -kf kangaroowork -o result.txt -wi 300 -wsplit -wmerge -rb 80000000000000000000 -re ffffffffffffffffffff -pub 037e1238f7b1ce757df94faa9a2eb261bf0aeb9f84dbf81212104e78931c2a19dc
```
You can use server/client app for Etarkangaroo https://github.com/Etayson/Server-Client-apps-for-Etarkangaroo
Purebasic v.5.31 required for compilation
