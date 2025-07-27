# Eevee vs Cycles

**Namen poglavja:** razumeš razliko med **Eevee** in **Cycles** – dvema render pogonoma v Blenderju – ter veš, kdaj uporabiti katerega. Naučiš se osnovnih nastavitev za svetlobo, sence, steklo in prosojnost, ter kako prilagoditi izgled v realnem času.

---

## Kaj sta Eevee in Cycles?

| Lastnost         | **Eevee**                     | **Cycles**                        |
|------------------|-------------------------------|-----------------------------------|
| Render tip       | *Real-time rasterizacija*     | *Path tracing (fizična simulacija)* |
| Hitrost          | Zelo hiter (za predogled)     | Počasnejši (kvaliteta nad hitrostjo) |
| Realizem         | Delno (odvisen od trikov)     | Visoka fizična natančnost         |
| Refleksije       | Lažne (Screen Space)          | Prave (ray-traced)                |
| Prosojnost       | Potrebna ročna nastavitev     | Naravna                          |
| Displacement     | Samo *bump map*               | Prava geometrija (displace)       |
| Osvetlitev HDRI  | Da                             | Da                                |
| Sence            | Lažje, a manj natančne        | Mehkejše, realistične             |

---

## Kako preklopiš

- *Render Properties* (ikona kamere) → zgoraj **Render Engine: Eevee / Cycles**

---

## Eevee – nastavitve za boljši izgled

Eevee je hiter, a potrebuje **ročno vključene učinke**, saj privzeto niso aktivni.

### Ključne nastavitve:
- **Screen Space Reflections** – za odseve
- **Ambient Occlusion** – za boljše sence v kotih
- **Bloom** – “svetle” svetlobe (npr. neon)
- **Soft Shadows** – mehkejše sence
- **Volumetrics** – za meglice in dim
- **Refraction** – omogoči lom svetlobe (steklo)

📍 Nahajajo se pod *Render Properties → Eevee*

---

## Cycles – kakovosten rezultat

Cycles simulira realno svetlobo z **path tracing** metodo.  
Podpira:
- Prave sence in odseve
- Pravo **displacement** geometrijo
- Realističen **SSS** (Subsurface Scattering)
- Globalno osvetlitev (GI)

🔸 Uporabi **GPU** če tvoj računalnik podpira CUDA / Optix / Metal:
*Edit → Preferences → System → Cycles Render Devices*

---

## Nasveti za renderje

| Namen                        | Priporočen render |
|-----------------------------|-------------------|
| Hiter predogled             | Eevee             |
| Realistična vizualizacija   | Cycles            |
| Spletni prikaz (igrivo)     | Eevee             |
| Portfelj / animacija        | Cycles            |

---

## Učinek: steklo

### Eevee:
1. V *Material Settings*:
   - **Blend Mode:** Alpha Blend / Hashed
   - **Screen Space Refraction:** ON
2. V *Render Properties*:
   - **Screen Space Reflections → Refraction:** ON
3. Material:
   - **Transmission > 0.9**
   - **Roughness** po potrebi (0.0 = čisto)

### Cycles:
- Ni potrebe po dodatnih trikih – samo Transmission + IOR nastavljen.

---

## Kratka vaja

1. Ustvari **kroglo**, dodaj material:
   - **Transmission = 1.0**
   - **Roughness = 0.1**
   - **IOR = 1.45**
2. Renderiraj v Eevee → popravi zgoraj opisane nastavitve
3. Preklopi na Cycles → primerjaj odseve, sence in lom svetlobe
4. Dodaj **HDRI svetlobo** (v *World Settings*) za boljši odboj

---

## Težave & rešitve

??? question "Steklo ne deluje v Eevee"
    Vklopi *Screen Space Refraction* v materialu in v *Render Properties*. Nastavi Blend Mode na **Alpha Blend/Hashed**.

??? question "Odsevi so napačni"
    Eevee uporablja **approximate reflections**. Uporabi **Reflection Cubemap** ali preklopi na **Cycles**.

??? question "Displacement ne deluje"
    Cycles mora imeti v materialu pod *Settings → Displacement: Displacement and Bump*. Potrebuješ **displacement mapo** in subdivision modifier.

??? question "Render traja predolgo"
    V *Render Properties → Sampling* znižaj **Render Samples** (npr. 64).  
    Vključi **Denoising** za boljši rezultat z manj šuma.

---

## Rezultat

Razumeš razliko med **Eevee** (real-time) in **Cycles** (fizični render), znaš prilagoditi nastavitve za steklo, sence in refleksije ter veš, kateri pogon uporabiti za hitrost ali realizem.

[**Naprej → Osvetlitev**](osvetljevanje.md){ .md-button .md-button--primary }
[← Nazaj: Vozlišča & UV](../materiali/vozlisca-in-uv.md){ .md-button }
