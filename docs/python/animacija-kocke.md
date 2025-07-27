# Animacija kocke s pomočjo `bpy`

**Namen poglavja:** naučiti se, kako animirati objekte v Blenderju s pomočjo Python kode (`bpy`). Dodali bomo **keyframe-e** za premik objekta, nastavljali **časovne točke (frame-e)** in ustvarili enostavno animacijo kocke.

---

## Kaj je keyframe?

**Keyframe** določa vrednost neke lastnosti (npr. lokacije) v določenem trenutku (frame-u). Blender nato sam vmes izračuna gibanje – to imenujemo **interpolacija**.

Primer:  
- Frame 1 → kocka na X = 0  
- Frame 50 → kocka na X = 5  
→ Blender jo gladko premika od točke A do B.

---

## Osnovna animacija: premik kocke

```python
import bpy

# Resetiraj sceno
bpy.ops.object.select_all(action='SELECT')
bpy.ops.object.delete(use_global=False)

# Dodaj kocko
bpy.ops.mesh.primitive_cube_add(location=(0, 0, 0))
cube = bpy.context.active_object

# Nastavi prvi keyframe (X = 0 na frame 1)
cube.location.x = 0
cube.keyframe_insert(data_path="location", frame=1)

# Nastavi drugi keyframe (X = 5 na frame 50)
cube.location.x = 5
cube.keyframe_insert(data_path="location", frame=50)
```

Kaj počne koda? 

- ustvari kocko
- nastavi njeno lokacijo na X = 0 in doda keyframe v `frame 1` 
- premakne kocko na X = 5 in doda keyframe v `frame 50`

Med tema točkama se kocka samodejno premika.

## Spreminjanje hitrosti animacije

Premik med dvema frame-oma je linearen – lahko pa spremeniš vrsto interpolacije (glej napredno).

Če želiš animacijo hitrejšo ali počasnejšo:

- krajši razmik med frame-i → hitreje
- daljši razmik → počasneje

## Dodatno: rotacija ali skaliranje

Lahko animiraš karkoli: rotacijo, velikost (scale), materiale ...

```python
# Rotacija (okoli Z)
cube.rotation_euler.z = 3.14  # 180 stopinj
cube.keyframe_insert(data_path="rotation_euler", frame=50)
```

## Vaja: kocka se dvigne in zavrti

1. Ustvari kocko v točki (0, 0, 0)
2. Na frame 1:
    - location Z = 0
    - rotation = 0
3. Na frame 60:
    - location Z = 3
    - rotation Z = 360 stopinj (6.28 rad)
4. Uporabi `keyframe_insert` za `location` in `rotation_euler`

## Težave & rešitve
??? question "Animacija ne deluje"
    - Preveri, ali si pravilno vstavil keyframe (.keyframe_insert(...))
    - Si v pravem objektu? Uporabi bpy.context.active_object

??? question "Kocka se samo premakne brez animacije"
    - Morda si pozabil nastaviti več frame-ov
    - Animacija se vidi v Timeline (spodaj)

??? question "Kamera ne sledi objektu"
    - Uporabi Follow Path constraint ali animiraj kamero ločeno

## Rezultat 

Znaš z `bpy` ustvariti animacijo z uporabo keyframe-ov. Obvladaš premikanje objekta po sceni, osnovno rotacijo ter razumeš osnovni princip 
animacije v Blenderju.

[**Naprej → Piramida (mreža)**](../python/piramida-mreza.md){ .md-button .md-button--primary }
[← Nazaj: bpy uvod](bpy-uvod.md){ .md-button }