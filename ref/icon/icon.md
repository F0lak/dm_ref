## icon object

An `/icon` object is created by loading an icon file into
memory for direct access and manipulation. In order to be displayed, an
`/icon` object always gets converted back into an icon file; this
happens automatically when you assign atom.icon to an `/icon` object,
since that variable may only refer to a static icon file, rather than a
dynamic memory object. 

To create an `/icon` object, simply use
`new/icon()`, or the short-cut `icon()` proc. The following example
loads an icon file, reddens it, and then assigns it back to the
player\'s icon, which implicitly creates a new icon file.
### Example:

```dm
mob/verb/test()
   var/icon/I = new('player.dmi')
   I.Blend(rgb(40,0,0))
   usr.icon = I
```
 
Note that merely displaying different icon states or directions can generally be achieved
without any icon manipulation, which saves quite a bit of overhead. For
example, the variables `atom.icon_state` and `atom.dir` can be used to
control how `atom.icon` is displayed, without any need for generating a
new icon file. 

> [!NOTE]
> Anything you can do with an atom var instead of using icon
manipulation procs will usually perform much better. Games that use the
new methods use fewer resources, use less memory, and also usually look
better too.

Many things that used to require icon
manipulation may not need you to do so anymore, as DM has evolved new
capabilities.
| Operation | /icon proc | New method |
| --- | --- | --- |
|  Multiplying by color | [`Blend`](/ref/icon/proc/Blend.md) or [SetIntensity](/ref/icon/proc/SetIntensity.md) procs | [color](/ref/atom/var/color.md)  var |
|  Adding color | [Blend](/ref/icon/proc/Blend.md) proc | [color](/ref/atom/var/color.md) var (using [color matrix](/ref/notes/color-matrix.md) ) |
|  Applying color matrix | [MapColors](/ref/icon/proc/MapColors.md) proc | [color](/ref/atom/var/color.md) var (using [color matrix](/ref/notes/color-matrix.md) ) |
|  Rotation | [Turn](/ref/icon/proc/Turn.md) proc | [transform](/ref/atom/var/transform.md) var | Flipping horizontal/vertical | [Flip](/ref/icon/proc/Flip.md) proc | [transform](/ref/atom/var/transform.md) var |
|  Scaling | [Scale](/ref/icon/proc/Scale.md) proc | [transform](/ref/atom/var/transform.md) var |
|  Overlaying/underlaying another icon | [Blend](/ref/icon/proc/Blend.md) proc + `ICON_OVERLAY`| Overlay/underlay + [KEEP_TOGETHER](/ref/atom/var/appearance_flags.md), or [Layering filter](/ref/notes/filters/layer.md) |

> [!TIP] 
> **See also:**
> +   [procs (icon)](/ref/icon/proc.md) 
> +   [icons](/ref/DM/icon.md) 
> +   [image objects](/ref/image.md) 
> +   [stddef.dm file](/ref/appendix/stddef%2edm.md) 