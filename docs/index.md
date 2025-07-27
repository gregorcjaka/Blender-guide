# Blender vodič za začetnike

<div align="center" markdown>

**Praktični spletni priročnik za prve korake v Blenderju**  
Od osnove modeliranja do materialov, osvetlitve, renderja in mini primerov z `bpy`.

[Začni z osnovami →](osnove-modeliranja/uvod.md){ .md-button .md-button--primary }
[Preskoči na materiale](materiali/principled-bsdf.md){ .md-button }
[Python dodatki](python/bpy-uvod.md){ .md-button }

</div>

---

## Kaj je cilj tega vodiča?

- Da v **nekaj sejah** spoznaš osnove 3D‑delovnega toka v Blenderju.  
- Da **samostojno** izdelaš preprost model, mu dodaš **material**, ga osvetliš in **renderiraš**.  
- Da vidiš, kako lahko z nekaj vrsticami **Pythona (`bpy`)** avtomatiziraš enostavne naloge.

!!! tip "Kaj pričakovati"
    Vodič je **praktičen** in izdelan **korak‑za‑korakom**. Pri vsaki temi najdeš cilj, korake, rezultat, pogoste težave in (neobvezno) mini Python rešitev.

---

## Komu je namenjen?

- Popolnim začetnikom v 3D in uporabnikom, ki **prvič** odpirajo Blender.  
- Tistim, ki želijo **hiter, uporaben** pregled najpogostejših orodij.  
- Radovednim ustvarjalcem, ki želijo poskusiti **bpy** za mini avtomatizacijo.

---

## Predpogoji

- **Blender** (priporočena zadnja stabilna različica)  
- **Miška** (delo je bistveno lažje kot s touchpadom)  
- Za Python del: **osnovno razumevanje** koncepta spremenljivk in ukazov (neobvezno)

!!! note "Uporabne bližnjice (privzeta keymap)"
    **G** premik · **R** rotacija · **S** skala · **Ctrl+R** Loop Cut · **Ctrl+B** Bevel  
    Če uporabljaš prenosnik, razmisli o vklopu *Emulate Numpad* v Preferences.

---

## Kaj se boš naučil/-a

- :material-cube-outline: **Osnove modeliranja** – mreža (mesh), oglišča/robovi/ploskve, G/R/S, Loop Cut, Extrude, Bevel, Subdivision  
- :material-palette-outline: **Materiali & senčenje** – **Principled BSDF**, vozlišča, teksture, osnovni **UV‑unwrap**  
- :material-lightbulb-on-outline: **Osvetlitev & kamera** – razlike med **Eevee** in **Cycles**, 3‑točkovna osvetlitev, kadriranje  
- :material-image-outline: **Renderiranje** – izvoz slik/kratkih videov, denoise, priporočene nastavitve  
- :material-code-tags: **Python mini‑primeri** – premik/animacija objekta, ustvarjanje enostavne mreže, *shape keys*

---

## Struktura vodiča

<div class="grid cards" markdown>

-   :material-cube-outline: **Osnove modeliranja**
    ---
    Prvi koraki v 3D prostoru in ključna orodja.
    
    [Odpri →](osnove-modeliranja/uvod.md){ .md-button .md-button--primary }

-   :material-palette-outline: **Materiali**
    ---
    Od osnov Principled BSDF do tekstur in UV‑mapiranja.
    
    [Odpri →](materiali/principled-bsdf.md){ .md-button .md-button--primary }

-   :material-spotlight-beam: **Render**
    ---
    Eevee vs Cycles, luči, kamera in končni izvoz.
    
    [Odpri →](render/eevee-vs-cycles.md){ .md-button .md-button--primary }

-   :material-code-tags: **Python (neobvezno)**
    ---
    Isti cilji, doseženi z nekaj vrsticami `bpy` kode.
    
    [Odpri →](python/bpy-uvod.md){ .md-button .md-button--primary }

</div>

---

## Kako uporabljati vodič

1. Odpri poglavje na levi in **sledi korakom**.  
2. Po vsakem sklopu **primerjaj rezultat** s sliko ali kratkim videom.  
3. Uporabi blok **“Težave & rešitve”**, ko se zatakne.  
4. Po želji odpri isti primer v **Python** zavihku.

=== "GUI"
    - Izberi objekt → **G/R/S** za transformacije  
    - Dodaj **Bevel** in preveri robove  
    - Uporabi **Subdivision** in *support loops*

=== "Python"
    ```python
    import bpy
    cube = bpy.data.objects.get("Cube")
    if cube:
        cube.location.x += 1.0
        bpy.context.view_layer.update()
    ```

---

## Prenosi in primeri

- `.blend` datoteke po poglavjih: `assets/blend/...`  
- Screenshoti: `assets/img/...`

!!! example "Kaj lahko izdelaš po prvih sklopih"
    - Enostaven hard‑surface model z urejeno topologijo  
    - Material z **Principled BSDF** in teksturo  
    - Osvetljen prizor s 3‑točkovno postavitvijo  
    - Render PNG ali kratek MP4 posnetek  
    - (Neobvezno) Premik/animacija objekta z `bpy`

---

## Pogoste težave in hitre rešitve

??? question "Subdivision “zmehča” robove"
    Dodaj **support loops** (Ctrl+R) ali uporabi **Edge Crease** na kritičnih robovih.

??? question "Render je temen ali “noisy”"
    Povečaj **Samples**, vključi **Denoise**, dodaj/uravnaj luči, preveri ekspozicijo.

??? question "Bližnjice ne delujejo"
    Preveri **Preferences → Keymap** (OS razlike), *Emulate Numpad*, *Industry Compatible*.

??? question "Python skripta nič ne naredi"
    Preveri, da je **objekt izbran**, da si v pravem **načinu** (Object/Edit) in odpri **Console/Info** za napake.

---

## Priporočeni vrstni red

<p class="btn-gap" align="center" markdown>
[**Začni tukaj → Uvod v osnove modeliranja**](osnove-modeliranja/uvod.md){ .md-button .md-button--primary }
[Materiali – Principled BSDF](materiali/principled-bsdf.md){ .md-button }
[Render – Eevee vs Cycles](render/eevee-vs-cycles.md){ .md-button }
[Uvod v `bpy`](python/bpy-uvod.md){ .md-button }
</p>


---

<div align="center" markdown>
Želim ti prijetno učenje in ustvarjanje — srečno! :material-cube-scan: :material-lightbulb-on-outline: :material-camera-outline:
</div>
