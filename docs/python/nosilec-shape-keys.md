# Nosilec (Shape Keys)

**Namen poglavja:** spoznati uporabo **Shape Keys** v Blenderju s pomočjo `bpy`. Uporabni so za deformacijo objekta – v tem primeru bomo ustvarili **nosilec iz kvadra**, ki se sčasoma **upogne** s pomočjo animiranega Shape Key-a.

---

## Kaj so Shape Keys?

Shape Keys (tudi morph targets) so shranjene različice geometrije. Blender jih uporablja za:
- animacijo obraznih izrazov
- deformacijo objektov (npr. nosilec, cev)
- mešanje med oblikami skozi čas

---

## Primer: nosilec, ki se upogne

```python
import bpy

# Počisti sceno
bpy.ops.object.select_all(action='SELECT')
bpy.ops.object.delete(use_global=False)

# Dodaj kvader dimenzij 1x1x5 (nosilec)
bpy.ops.mesh.primitive_cube_add(size=1, location=(0, 0, 0))
obj = bpy.context.active_object
obj.scale = (0.5, 0.5, 2.5)
bpy.ops.object.transform_apply(scale=True)

# Podmreži kvader (rezanje po Z osi)
bpy.ops.object.mode_set(mode='EDIT')
bpy.ops.mesh.subdivide(number_cuts=10)
bpy.ops.object.mode_set(mode='OBJECT')

# Dodaj Shape Keys
obj.shape_key_add(name="Basis")           # osnovna oblika
bend = obj.shape_key_add(name="Upogib")   # deformirana oblika

# Ukrivi zgornji del nosilca (premakni vertekse)
for i, v in enumerate(obj.data.vertices):
    z = v.co.z
    if z > 0:
        factor = z / 2.5  # normalizirano (0–1)
        bend.data[i].co.x += 0.2 * factor**2  # ukrivljanje na X

# Animacija Shape Key-a
bend.value = 0.0
bend.keyframe_insert(data_path="value", frame=1)

bend.value = 1.0
bend.keyframe_insert(data_path="value", frame=50)
```

Kaj počne koda? 

- Doda kvader, dimenzij 1×1×5
- Ga subdividira vzdolž višine (Z)
- Ustvari `Shape Key`, ki upogne zgornji del v lok
- Dodaja keyframe-e:
    - `frame 1`: brez deformacije
    - `frame 50`: polno upognjen

## Vaja: spremeni deformacijo

1. Namesto upogibanja v X smeri, poskusi `co.y += ...`
2. Poskusi eksperimentirati z različnimi krivuljami (`sin(z)`, `z**3`, ...)
3. Dodaj več Shape Key-ov (npr. stranski premik, širjenje) in jih združi

## Težave & rešitve

??? question "Ni deformacije"
    - Preveri, ali si v `Upogib` Shape Key-u spreminjal točke
    - Preveri `.value = 1.0` in `keyframe_insert`

??? question "Upogib je premočan"
    - Zmanjšaj vrednost `+= 0.2 * factor**2`
    - Uporabi manj rezov (manj `subdivide`), da bo mehkejša deformacija

??? question "Ni animacije"
    - Preveri Timeline in Play (`Space`)
    - Ključni okvirji morajo biti na `Upogib.value`

## Rezultat 

Znaš ustvariti lasten objekt (nosilec), ga razdeliti na dele, deformirati njegovo obliko s Shape Key-om in ustvariti animacijo prehoda med dvema oblikama. S tem si osvojil/-a pomemben element za proceduralno animacijo in organsko gibanje.

[← Nazaj: Piramida (mreža)](piramida-mreza.md){ .md-button }