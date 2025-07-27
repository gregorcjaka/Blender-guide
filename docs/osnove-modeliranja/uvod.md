# Osnove 3D modeliranja

**Namen poglavja:** razumeti, kaj Blender je, kako so 3D objekti zgrajeni (mreža/mesh), kako odpreti prazen projekt in se orientirati po vmesniku, ter kakšna je razlika med **Object** in **Edit** načinom. To je izhodišče za naslednji poglavji.

---

## Kaj je Blender?

**Blender** je brezplačno, odprtokodno orodje za 3D ustvarjanje. Uporablja se za
modeliranje, materiale in senčenje, animacijo, simulacije, osvetljevanje, renderiranje
in še več. Deluje v več okoljih (Windows, macOS, Linux) in vključuje dva glavna
renderirna pogona: **Eevee** (hiter, real‑time) in **Cycles** (fizično bolj
natančen). Blender podpira nedestruktivno delo preko **modifikatorjev** in omogoča
avtomatizacijo z **Python** (`bpy`), kar pride prav kasneje.

---

## Kaj je mreža (mesh)?

Večina 3D objektov v Blenderju je zgrajena iz **mreže**, ki jo sestavljajo:
- **Oglišča (vertices)** – točke v prostoru,
- **Robovi (edges)** – povezave med oglišči,
- **Ploskve (faces)** – površine, navadno trikotniki ali štirikotniki.

Dodatni pojmi, ki jih je koristno poznati že zdaj:
- **Normale**: smer, v katero “gleda” ploskev (pomembno pri senčenju in renderiranju).
- **Trikotniki/štirikotniki/ngoni**: priporočljivo je, da začetnik večino površin ohranja kot **štirikotnike (quads)**; trikotniki in n‑kotniki so pogosto uporabni, a zahtevajo več pozornosti.
- **Točka izvora (origin)**: referenčna točka objekta; vpliva na vrtenje, skaliranje in poravnavo.

---

## Prvi zagon in orientacija po vmesniku

Ko odpreš nov projekt, boš v sceni videl **kocko**, **kamero** in **luč**. Glavna območja:
- **3D Viewport** – kjer delaš z objekti.
- **Outliner** – seznam vseh objektov v sceni (organizacija po **Collections**).
- **Properties** – nastavitve za sceno, materiale, modifikatorje, render itd.
- **Timeline** – časovnica (za animacije; za zdaj jo lahko ignoriraš).

**Navigacija po pogledu** (3D Viewport):
- Vrtenje pogleda: srednji gumb miške (MMB).
- Premik pogleda (pan): **Shift + MMB**.
- Zoom: kolešček miške ali **Ctrl + MMB**.
- Hiter skok v ortografske poglede: **Numpad 7/1/3** (zgoraj/spredaj/desno).
- Preklop **Perspective/Orthographic**: **Numpad 5**.

!!! note "Perspective vs Orthographic"
    Perspektivni pogled daje občutek globine (oddaljeni predmeti so manjši).
    Ortografski pogled odstrani perspektivo in je boljši za natančno poravnavo in merjenje.

---

## Načini dela: Object vs Edit

- **Object Mode**: delaš z **objektom kot celoto** (premikanje, rotacija, skala, dodeljevanje materialov, modifikatorji, organizacija po kolekcijah).
- **Edit Mode**: urejaš **strukturo mreže** – oglišča, robove in ploskve izbranega objekta.

Preklop med načinoma: **Tab**.  
V *Edit Mode* lahko izbiraš po komponentah:
- **Vertex Select** (oglišča), **Edge Select** (robovi), **Face Select** (ploskve).

---

## Osnovna načela topologije

- **Cilj je urejen “tok robov” (edge flow)** – ploskve naj sledijo obliki.
- **Prednost quads** – štirikotniki se dobro obnašajo pri deformacijah in kasnejši subdiviziji.
- **Enakomerna gostota** – izogibaj se ekstremno velikim ploskvam poleg zelo gostih območij.
- **Manifold geometrija** – pazi, da mreža tvori “zaprte” volumne, razen ko namenoma modeliraš odprte površine.
- **Konzistentne normale** – če opaziš “temne madeže” pri senčenju, znajo biti ploskve obrnjene narobe (o popravljanju bomo kasneje).

---

## Težave & rešitve

??? question "Ne morem več vrteti ali pomikati pogleda"
    Preveri, ali imaš vklopljen *Emulate 3 Button Mouse* (če nimaš srednjega gumba).  
    **Edit → Preferences → Input → Emulate 3 Button Mouse.**

??? question "Zgubil/-a sem objekt iz pogleda"
    Izberi objekt v **Outlinerju** in pritisni **Numpad . (Period)** za *Frame Selected*.

??? question "V Edit Mode ne morem izbrati ploskev/robov"
    Preveri način izbire (Vertex/Edge/Face Select v zgornji vrstici Viewporta) in ali si res v **Edit Mode**.

??? question "Objekt je zelo temen ali ima “luknje”"
    Lahko gre za nekonsistentne **normale** ali prekrivajoče se ploskve. Oboje bomo reševali kasneje; za zdaj je dovolj, da prepoznaš simptom.

---

## Rezultat

Po tem uvodu razumeš:
- kaj Blender je in za kaj ga uporabljamo,
- kako je 3D objekt zgrajen iz mreže,
- kako se znajti v vmesniku in premikati po pogledu,
- razliko med **Object** in **Edit** načinom,
- osnovna načela dobre topologije.

[**Naprej → Transformacije**](transformacije.md){ .md-button .md-button--primary }
[Modelirna orodja](orodja.md){ .md-button }
