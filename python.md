# Python Hacks

How to issue shell commands programatically without feeling dirty from excessive bash usage.

## Oh Noes! I Deleted My Git Branch. It Contained a Brill Function Called `convert`

```python
 
import os

for x in xrange(0, 100):
	cmd = "git show HEAD@{{{}}}|grep convert".format(x)
	print(cmd)
	os.system(cmd)
```
