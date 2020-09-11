---
title: xluntils  module 'xlutils' has no attribute 'copy'
date: 2020-06-05 16:13:16
tags:
 -python
 -xlutils
categories: python
---
# xluntils  module 'xlutils' has no attribute 'copy' 解决

打开xluntils 包的init.py文件会发现 init.py文件是空的，向里面添加以下代码，问题解决

```python
from .compat import *
from .copy import *
from .display import *
from .filter import *
from .margins import *
from .save import *
from .styles import *
from .view import *
```



