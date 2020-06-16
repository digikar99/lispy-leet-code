# 05 Longest Palindromic Substring

The Problem: https://leetcode.com/problems/longest-palindromic-substring/

Motivation: https://www.geeksforgeeks.org/longest-palindrome-substring-set-1/

```lisp
(in-package :leet-code)
(defun longest-palindromic-substring (string)
  (let* ((len (length string))
         (dp (make-array (list len len)
                         :initial-element nil)))
    ;; [dp i j] corresponds to a string starting at i and ending at j
    ;; both inclusive
    (iter outer
          (for i from (- len 2) downto 0)
          (iter (for j from 1 below len)
                (setf [dp i j]
                      (cond ((= i j) t)
                            ((= (1+ i) j)
                             (char= [string i]
                                    [string j]))
                            (t
                             (and [dp (1+ i) (1- j)]
                                  (char= [string i]
                                         [string j])))))
                (when [dp i j]
                  (in outer
                      (finding (list i j) maximizing (- j i) into start-end))))
          (finally
           (destructuring-bind (start end) start-end
             (return-from outer (subseq string start (1+ end))))))))
```

Pointer: What is the condition on i+1..j-1 for i..j to be a palindrome?
