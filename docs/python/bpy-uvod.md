# Uvod v `bpy`

**Namen poglavja:** spoznati osnove skriptnega jezika `bpy`, ki omogoča programiranje in avtomatizacijo v Blenderju. Naučil/-a se boš ustvariti preprost objekt, spremeniti njegove lastnosti in razumeš, kako `bpy` komunicira s 3D-sceno.

---

## Kaj je `bpy`?

`bpy` (Blender Python) je **vgrajena Python knjižnica**, ki omogoča dostop do skoraj vseh funkcij Blenderja — od ustvarjanja objektov do renderiranja, animacij in urejanja materialov.

> ✅ Če znaš osnovni Python, se lahko hitro naučiš avtomatizirati procese v Blenderju.

---

## Kje pišemo `bpy` kodo?

1. **Scripting** zavihka v Blenderju:
   - Odpri *Layout → Scripting*
   - Uporabi vgrajen **Text Editor**
   - Klikni **New**, napiši kodo
   - Klikni **Run Script**

2. **Python konzola**:
   - Nahaja se znotraj zavihka *Scripting*
   - Lahko direktno preizkušaš posamezne vrstice

---

## Prvi primer: kocka na novo

```python
import bpy

# Pobriši vse
bpy.ops.object.select_all(action='SELECT')
bpy.ops.object.delete(use_global=False)

# Dodaj novo kocko
bpy.ops.mesh.primitive_cube_add(size=2, location=(0, 0, 0))
```
Ta koda:

- izbriše vse obstoječe objekte
- doda novo kocko velikosti 2 v središče (0, 0, 0)

## Dodajanje in spreminjanje lastnosti

Nadgradimo prejšnjo skripto:

```python
cube = bpy.context.active_object
cube.name = "MojaKocka"
cube.location.x += 2
cube.scale = (1.5, 1.5, 0.5)
```

- `bpy.context.active_object`: trenutno izbrani objekt
- `.name`: preimenuje objekt
- `.location`, `.scale`, `.rotation_euler`: dostop do osnovnih lastnosti

## Primer: Premik več kock

V Blenderju deluje Python popolnoma običajno. Uporabimo **for** zanko:

```python
for i in range(5):
    bpy.ops.mesh.primitive_cube_add(size=1, location=(i * 2, 0, 0))
```

Ta skripta ustvari 5 kock zaporedoma ob osi X, vsako 2 enoti narazen.

## Prikaz objektov z materiali (napredno)

```python
mat = bpy.data.materials.new(name="RdeciMaterial")
mat.diffuse_color = (1, 0, 0, 1)  # RGBA

bpy.ops.mesh.primitive_uv_sphere_add(location=(0, 0, 0))
obj = bpy.context.active_object
obj.data.materials.append(mat)
```

Skripta v Blenderju ustvari nov material rdeče barve in doda UV sfero v središče scene. Nato dodeli ta material sferi, da je prikazana kot 
rdeča.


## Povezava s prejšnjim delom

Z `bpy` lahko avtomatiziraš vse, kar si do zdaj počel/-a ročno:

- ustvarjanje objektov
- postavljanje svetlobe in kamere
- dodajanje materialov
- renderanje
- animacije (naslednje poglavje)

## Vaja: naredi sceno s 3 kockami
1. Pobriši obstoječe objekte
2. Dodaj 3 kocke, razmaknjene ob X
3. Vsaki kocki nastavi različen scale
4. Preimenuj vsako
5. Dodaj rdeč material prvi, zelen drugi, moder tretji

## Težave & rešitve
??? question "Skript ne deluje"
    - Preveri, ali imaš pravilno uvožen bpy
    - Pazi na napačne zamike (Python je občutljiv na zamike)

??? question "Objekt ni ustvarjen"
    - Morda si v napačnem načinu (npr. Edit Mode). Pojdi nazaj v Object Mode.
    - Uporabi bpy.ops.object.mode_set(mode='OBJECT')

??? question "Koda vpliva samo na en objekt"
    - bpy.context.active_object deluje le, če je objekt izbran.
    Uporabi .objects["Ime"] za dostop po imenu.

## Rezultat

Znaš napisati osnovno `bpy` skripto, ustvariti objekte, jih poimenovati, prestavljati in jim dodeliti material. Pripravljen/-a si za naslednji korak: **animacija s kodo**.

[**Naprej → Animacija kocke s kodo**](../python/animacija-kocke.md){ .md-button .md-button--primary }
[← Nazaj: Kamera & render](../render/kamera-in-render.md){ .md-button }