tex-obj
======

An implementation of the object-oriented paradigm for `expl3` of the LaTeX3 project.

```tex
\nonstopmode \input expl3-generic \relax \ExplSyntaxOn % -*- expl3 -*-

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

\file_input:n { obj }

\obj_new:nn { rectangle }
  {
    length: int,
    width: int,
    stroke-color: color = black,
    fill-color: color = white
  }

\obj_new:nn { rectangle / rhombus }
  { angle: int = 45 }

\rhombus_new:Nn \l_demo_rhombus
  {
    length = 4,
    stroke-color = gray,
  }

    \msg_term:n { Expect:~ elements~of~`rectangle'~and~`rhombus' }
    \rhombus_show:N \l_demo_rhombus

\obj_method:nnn { rectangle } { get_field:NnN }
  { \obj_this:nN {#2} #3 }

    \msg_term:n { Expect:~`\string\obj_this:n'~definition }
    \cs_show:N \rectangle_get_field:NnN

\rectangle_get_field:NnN \l_demo_rhombus { fill-color } \l_tmpa_tl

    \msg_term:n { Expect:~white }
    \tl_show:N \l_tmpa_tl

\bye
```
