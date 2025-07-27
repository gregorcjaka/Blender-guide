# Piramida (mreža) s kodo

**Namen poglavja:** naučiti se ustvariti lasten 3D-objekt (v tem primeru piramido) tako, da ročno definiraš oglišča in ploskve v Pythonu. To je osnova za proceduralno modeliranje v Blenderju.

---

## Koncept: oglišča in ploskve

Objekt v Blenderju je zgrajen iz:
- **Vertices (oglišča)** – točke v prostoru (X, Y, Z)
- **Edges (robovi)** – povezave med oglišči *(opcijsko)*
- **Faces (ploskve)** – povezujejo več oglišč v ploskev

Pri `bpy` te podatke vstavimo kot sezname.

---

## Primer: koda za piramido

```python
import bpy
import bmesh

# Pobriši obstoječe objekte
bpy.ops.object.select_all(action='SELECT')
bpy.ops.object.delete(use_global=False)

# Koordinati oglišč (5 oglišč: 4 spodaj, 1 zgoraj)
verts = [
    (-1, -1, 0),  # spodaj levo
    (1, -1, 0),   # spodaj desno
    (1, 1, 0),    # zgoraj desno
    (-1, 1, 0),   # zgoraj levo
    (0, 0, 2)     # vrh piramide
]

# Ploskve (sklicujejo se na indekse oglišč)
faces = [
    (0, 1, 2, 3),  # spodnja ploskev (kvadrat)
    (0, 1, 4),     # stranica 1
    (1, 2, 4),     # stranica 2
    (2, 3, 4),     # stranica 3
    (3, 0, 4)      # stranica 4
]

# Ustvari novo mrežo in objekt
mesh = bpy.data.meshes.new(name="PiramidaMesh")
obj = bpy.data.objects.new("Piramida", mesh)

# Dodaj v sceno
bpy.context.collection.objects.link(obj)

# Ustvari geometrijo
mesh.from_pydata(verts, [], faces)
mesh.update()
```

Kaj počne koda? 

- Definira 5 oglišč
- Sestavi spodnji kvadrat in 4 trikotnike (stranice piramide)
- Ustvari novo `Mesh` in `Object`
- Doda jo v sceno in prikaže

## Vaja: spremeni obliko

1. Spremeni višino piramide (`Z` koordinata vrha)
2. Naredi širšo osnovo (spremeni `X` in `Y` spodnjih oglišč)
3. Namesto kvadrata poskusi osnovo narediti trikotno (3 oglišča spodaj + 1 vrh)

## Težave in rešitve

??? question "Objekt ni viden"
    - Morda si v napačnem pogledu – pritisni Numpad 0 za kamero ali Numpad 5 za perspektivo.
    - Preveri ali je objekt viden v Outlinerju.

??? question "Ploskve niso pravilno povezane"
    - Preveri vrstni red oglišč v faces. Pravilna orientacija = nasprotni kazalec urinega.

??? question "Objekt nima materiala"
    - Dodaj material kot v prejšnjem poglavju:
    `python mat = bpy.data.materials.new(name="TestMaterial") obj.data.materials.append(mat)`

## Rezultat

Znaš s `bpy` definirati oglišča in ploskve, ustvariti 3D mrežo in jo dodati v sceno. Osnovno razumeš podatkovno strukturo objektov v Blenderju in si naredil/-a prvi proceduralni model.

[**Naprej → Nosilce s shape keyi**](../python/nosilec-shape-keys.md){ .md-button .md-button--primary }
[← Nazaj: Animacija kocke](animacija-kocke.md){ .md-button }