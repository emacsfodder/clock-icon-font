[![](https://github.com/ocodo/ClockFace-font/raw/master/ClockFace-font-splash.png)](https://ocodo.github.io/ClockFace-font/)

# Clockicon

Using https://ocodo.github.io/ClockFace-font in Emacs

- [ ] Fetch/Install fonts if they're not installed.
  - https://ocodo.github.io/ClockFace-font/ClockFaceFonts.zip
- [ ] Provides custom faces for the icon fonts.
- [ ] Provide a function to insert the time as icon
- [ ] Provide a function to generate a propertized/overlay of time as icon

```lisp
(require 'cl-lib)

(defun clockicon-unicode (hours minutes)
  "Return clock icon unicode for HOURS and MINUTES."
  (let* ((minute (- minutes (% minutes 5)))
         (offset (+ (* (% hours 12) 12) (* 12 (/ minute 60)))))
       (+ offset #xE800)))

(defun clockicon-now-unicode ()
  "Return clock icon unicode for the time now."
  (cl-destructuring-bind
      (_ _ hour minute &rest n) (decode-time)
    (clockicon-unicode hour minute)))
    
(defface clock-icons '((t (:family ClockFace))) "ClockFace icons")
(defface clock-icons-solid '((t (:family ClockFaceSolid))) "ClockFaceSolid icons")
(defface clock-icons-rect '((t (:family ClockFaceRect))) "ClockFaceRect icons")
(defface clock-icons-rect-solid '((t (:family ClockFaceRectSolid))) "ClockFaceRectSolid icons")

```
