# My Keyboard Config (Dvorak)






```
(defcfg
  ;; For Linux
  input  (device-file "/dev/input/by-id/usb-Compx_2.4G_Wireless_Receiver-event-kbd")
  output (uinput-sink "My KMonad output"
    ;; To understand the importance of the following line, see the section on
    ;; Compose-key sequences at the near-bottom of this file.
    "/run/current-system/sw/bin/sleep 1 && /run/current-system/sw/bin/setxkbmap -option compose:ralt")
  cmp-seq ralt    ;; Set the compose key to `RightAlt'
  cmp-seq-delay 5 ;; 5ms delay between each compose-key sequence press

  ;; For Windows
  ;; input  (low-level-hook)
  ;; output (send-event-sink)

  ;; For MacOS
  ;; input  (iokit-name "my-keyboard-product-string")
  ;; output (kext)

  ;; Comment this if you want unhandled events not to be emitted
  fallthrough true

  ;; Set this to false to disable any command-execution in KMonad
  allow-cmd true
)


;; note : - check what you want to map in dvorak, and then use the character that is in location of that dvorak key (exact location, not the character) in QWERTY


(defalias
  mynum (layer-toggle numbers)
  back (around lalt left)
  wl (around (around lalt lctl) left)
  wr (around (around lalt lctl) right)
    
  
  arrow (layer-toggle arrows)

  
  ;; modding space
  mysyb (layer-toggle symbols)
  mc1 #(bspc @mysyb)
  sd (around bspc @mysyb)
  mysy (tap-hold-next-release 350 pause @mc1)
  cspc (around spc @mysy)
  cb (around lctl bspc)
  
)
(defsrc
  esc  f1   f2   f3   f4   f5   f6   f7   f8   f9   f10  f11  f12
  grv  1    2    3    4    5    6    7    8    9    0    -    =    bspc  pause  home pgup
  tab  q    w    e    r    t    y    u    i    o    p    [    ]    \     del  end  pgdn
  caps a    s    d    f    g    h    j    k    l    ;    '    ret
  lsft z    x    c    v    b    n    m    ,    .    /    rsft                 up       
  lctl lmet lalt           spc            ralt rmet cmp  rctl            left down rght
)

(deflayer mine
 esc    home end  @wl  @wr  f5   f6   f7   f8   f9   f10  f11  f12
  grv    _    _    S--  -    S-9  _    S-0  =    S-=  _    _    _   bspc  pause  home pgup
  tab    q    w    e    r    t    y    u    i    o    p    esc  ]    del     del  end  pgdn
  @back  a    s    d    f    g    h    j    k    l    ;    '    ret
  lsft   z    x    c    v    b    n    m    ,    .    /    rsft                 up       
  lmet   lalt @mynum         @cspc          lctl rmet cmp lmet            left down rght
)
(deflayer symbols 
  _    _    _    _    _    _    _    _    _    _     _    _    _
  _    _    _    _    _    _    _    _    _    _     _    _    _    @cb   _    _    _
  _    !    @    S-3  $    %    _    7    8    9     _    _    _    _     _    _    _
  _    ^    '    S-]  ]    |    _    4    5    6     _    _    _
  _    S-[  [    S-8  &    \    0    1    2    3     _    _                    _
  _    _    _              _              _    _     _    _               _    _    _
)

(deflayer numbers 
  _    _    _    _    _    _    _    _    _    _    _    _    _
  _    _    _    _    _    _    _    _    _    _    _    _    _    @cb   _    _    _
  _    S-q  _    _    _    _    _    _    up   _    _    _    _    _     _    _    _
  _    C-;  C-i  C-b  C-.  _    _    left down right _    _    _
  _    C-/  C-t  _    _    _    _    _    _    _    _    _                    _ 
  _    _    _              _              _    _    _    _               _    _    _
)
(deflayer arrows
  _    _    _    _    _    _    _    _    _    _    _    _    _
  _    _    _    _    _    _    _    _    _    _    _    _    _    _     _    _    _
  _    _    _    _    _    _    _    _    _    _    _    _    _    _     _    _    _
  _    _    _    _    _    _    _    _    _    _     _    _    _
  _    _    _    _    _    _    _    _    _    _    _    _                    _
  _    _    _              _              _    _    _    _               _    _    _
)

```
