![]

# Clockicon

Using https://ocodo.github.io/ClockFace-font in Emacs

- [ ] Fetch/Install fonts if they're not installed.
- [ ] Provides custom faces for the icon fonts.
  ```lisp
  (defface clockicon-normal)
  (defface clockicon-solid)
  (defface clockicon-rect)
  (defface clockicon-rectsolid)
  ```
- [ ] Provide a function to insert the time as icon
  ```lisp
  (defun clockicon-insert-time (time &optional clock-style)
    "Insert TIME as a clock icon, optionally specify CLOCK-STYLE.
  Which can be one of `:normal', `:solid', `:rect', `:rect-solid'."
    (interactive)
    ;;  ... code
  ```
- [ ] Provide a function to generate a propertized/overlay of time as icon
  ```lisp
  (defun clockicon-time (time &optional clock-style)
    "Generate TIME as a clock icon propertized string, 
  optionally specify CLOCK-STYLE.
  Which can be one of `:normal', `:solid', `:rect', `:rect-solid'."
    (interactive)
    ;;  ... code
  ```
  
```lisp
(defun clockicon-unicode (hours minutes)
  "Return clock icon unicode for HOURS and MINUTES."
  (let* ((minute (- minutes (% minutes 5)))
         (offset (+ (* (% hours 12) 12) (* 12 (/ minute 60)))))
       (+ offset #xE800)))
```
