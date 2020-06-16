# lispy-leet-code

```lisp
(ql:quickload '(:alexandria :iterate :reader))
(reader:enable-reader-syntax 'get-val 'lambda) ; evaluate in REPL than C-c C-c
(defpackage :leet-code (:use :cl :alexandria :iterate))
(in-package :leet-code)
```

For best results, use emacs with [polymode](https://github.com/polymode/polymode) / poly-markdown-mode. Happy lisping!


