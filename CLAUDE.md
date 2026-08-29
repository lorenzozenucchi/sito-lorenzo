# sito-lorenzo — il sito personale di Lorenzo Zenucchi

## Cos'è

Una sola pagina, `index.html`, più tre pagine di esempio in `esempi/`.
HTML/CSS/JS vanilla, nessun build, nessuna dipendenza: si apre con doppio clic.
Il repository sarà pubblico.

## A cosa serve (determina ogni scelta)

Non è un canale di acquisizione: nessuno ci arriva da Google. Ci si arriva dal
**QR sul retro del biglietto da visita** che Lorenzo lascia in negozio dopo una
visita. Chi apre la pagina l'ha in mano da pochi minuti — spesso non il
titolare, ma il figlio o il socio a cui ha girato il cartoncino.

Il sito quindi non deve vendere da zero: deve **confermare** una vendita già
iniziata di persona e dare il modo di richiamare. Da qui tre conseguenze:

- l'ordine delle sezioni è la sequenza delle domande che il titolare si fa
  scorrendo col pollice: chi è → com'è un sito suo → cosa gli tocca fare →
  quanto costa → che faccia ha → come lo chiama. Non si riordina;
- **il sito è l'unico campione del prodotto**. Lorenzo ha deciso di non mostrare
  lavori di clienti reali: la prova che sa fare siti è il sito stesso. Se si apre
  in un istante e si legge con una mano sola, il titolare ha già capito. Non c'è
  una rete di sicurezza fatta di referenze;
- il 90% dei visitatori è da telefono. Mobile-first non è una preferenza.

## Identità visiva: il biglietto, portato a dossier tecnico

Chi ha il cartoncino in mano deve riconoscere la pagina in mezzo secondo, prima
ancora di leggerla: quell'identità non si sostituisce, si porta a un livello di
cura più alto. La direzione non è una vetrina ma **il dossier tecnico di un
progetto** — coerente con "web designer & developer" e con l'idea che Lorenzo le
cose le costruisce. L'illustrazione a tratto (portatile + smartphone) e la riga
delle sei categorie restano la citazione diretta di fronte e retro del biglietto.

**Palette a tre ruoli**, tutta derivata dal cartoncino:
- *fondo* — verdi profondi (`--verde-profondo` #0a2424, `--verde-ombra` per le
  ombre e i gradienti, due verdi-carta per i pannelli pieni);
- *accento* — oro (`--oro` #d9b96f) e un oro chiaro per gli stati in evidenza;
- *testo* — crema caldo (`--crema`, mai bianco puro) per il primario e
  `--muschio`, un verde-grigio con dominante di tinta e non un grigio neutro,
  per il secondario.

**Tema fisso, scuro.** Il sito non risponde al tema chiaro/scuro del dispositivo:
è legato a un oggetto di carta già stampato con quei colori esatti. I colori si
dichiarano una volta sola in `:root`, mai condizionati al tema di sistema.

**Tipografia a tre voci.** Cormorant Garamond solo per i titoli grandi (nome,
payoff, h2 e i titoli dei pannelli), non per il corpo; Work Sans per il testo;
IBM Plex Mono per tutto ciò che è dato tecnico — i due prezzi, le cifre 01/02/03
degli esempi e dei passi, le etichette piccole maiuscole. I numeri devono
leggersi come cifre su una tavola tecnica, non come prosa. Il payoff ha una
**scala drammatica**, pensata come il titolo di una copertina: pesa per
contrasto, non solo per dimensione assoluta — nome, ruolo e intro si
ridimensionano apposta, per non competere con quel momento.

**Due segni ricorrenti, entrambi discreti:**
- i **segni d'angolo** (`.cornice` + quattro `.segno`): quattro piccoli angoli in
  oro come i crocini di registro su una bozza di stampa, al posto degli angoli
  arrotondati. Solo sui tre elementi che meritano l'enfasi — cornice
  dell'illustrazione, le tre card di esempio, il riquadro prezzo in evidenza. Se
  finiscono ovunque smettono di significare qualcosa;
- lo **sfondo topografico** (`.terreno`): poche curve di livello fisse, opacità
  sotto il 10%, che richiamano la valle. Sta dietro alle zone senza pannello
  pieno e deve restare quasi impercettibile: mai in competizione col testo.

**Una grana fotografica sopra tutta la pagina.** Un canvas nativo (non SVG, non
un'immagine scaricata) disegna rumore casuale e lo sovrappone a tutta la pagina
in blend mode, a bassissimo fotogramma: aggiunge tessitura senza toccare i
colori sotto, la differenza tra una superficie piatta e una stampa di pregio.
Deve restare percepibile solo se la si cerca.

**Movimento con misura**, un'idea forte invece di tanti effetti: l'illustrazione
si disegna da sola al caricamento (stroke-dashoffset misurato a runtime), gli
elementi dell'apertura entrano in sequenza, ogni pannello sotto l'apertura entra
**una volta sola** quando arriva a schermo, e le card/riquadri/contatti hanno un
piccolo sollevamento con accento sui segni d'angolo al passaggio. Al primo
caricamento un **sipario** — due pannelli bordati d'oro, creati via JavaScript e
mai presenti nel markup statico — si apre dal centro verso i lati in circa sei
decimi di secondo, una volta sola per sessione di navigazione (`sessionStorage`).
Su schermi con puntatore preciso (`hover:hover` e `pointer:fine`, mai su touch)
l'illustrazione risponde con una lieve inclinazione al movimento del cursore e
il pulsante d'azione principale gli si avvicina di pochi pixel quando ci passa
vicino: un'eco minima di **profondità al gesto**, assente su telefono. Due regole
non negoziabili: tutto rispetta `prefers-reduced-motion`, e il `<noscript>` in
testa rende visibili i pannelli `.reveal` — senza JavaScript la pagina resta
leggibile, perché il contenuto viene prima dell'animazione.

Esiste anche un foglio-offerta cartaceo con una palette diversa (crema e
bordeaux): **non è il riferimento**. Il riferimento è il biglietto. Del
foglio-offerta si riusa l'impianto della sezione prezzi, non i colori.

## Regole che non si negoziano

- **Nomi di fantasia negli esempi.** Le tre pagine in `esempi/` sono adattate dai
  template di `~/locali/demo-factory/templates/` (sola lettura), ma nomi,
  indirizzi, orari e recensioni sono inventati e i paesi sono generici
  ("Val Seriana (BG)", mai un comune preciso). Ogni pagina porta in fondo una
  barra fissa che dichiara che l'attività non esiste e riporta a `index.html`.
  Le 115 demo in `demo-factory/demos/` sono personalizzate su attività reali che
  in gran parte non sono clienti: **non si usano e non se ne copiano i dati**.
- **Niente claim non verificabili.** Nessun numero di clienti, nessuna referenza,
  nessun logo, nessun "da 10 anni nel settore". Lorenzo ha un solo cliente e ha
  deciso di non esporlo: un claim gonfiato su una pagina che vende onestà è il
  danno peggiore possibile.
- **Nessun tracker, nessun cookie, nessun servizio di terze parti.** Niente
  Analytics, niente pixel, niente mappe embed, niente widget. L'unica richiesta
  di rete esterna è Google Fonts (preconnect + una sola `css2`). L'assenza del
  cookie banner è essa stessa una dimostrazione, ed è dichiarata nel footer:
  se un domani si aggiunge un tracker, va corretto anche quel footer.
- **La promo vive in due punti, entrambi marcati.** Prezzo barrato, 390 € e
  la riga "primi 5 clienti" compaiono nel blocco `BLOCCO PROMO` (sezione
  Quanto costa) e nel richiamo `BLOCCO PROMO HERO` (apertura, vicino ai
  pulsanti). Quando il quinto cliente firma quella frase diventa falsa e si
  porta dietro la credibilità del resto: le istruzioni per aggiornare
  entrambi i punti sono nel commento in cima a `index.html`.
- Convenzioni tecniche condivise: `~/produzione/convenzioni-tecniche.md`. Si
  applicano le regole generali (file autonomo, CSS inline, variabili `:root` in
  italiano, reset, `prefers-reduced-motion`, mobile-first, immagini sotto i
  300-400 KB). **Non** si applicano le sue "sezioni minime": sono pensate per il
  sito di un locale, questo è un altro tipo di pagina.
- Il subagent `sito-builder` di `~/produzione` **non si usa qui**: pretende un
  `brief.md`, impone le sezioni di un sito da locale e chiude con un invito
  "verso Lorenzo", che qui sarebbe un invito verso sé stesso.

## In sospeso

- **Dominio ed email.** Candidato `lorenzoweb.it`, da verificare su Cloudflare.
  Finché non c'è, la pagina usa `lorenzozenucchi00@gmail.com` e i tag
  `canonical` e `og:url` restano commentati nel `<head>`. Le istruzioni per
  aggiornarli sono nel secondo commento in cima a `index.html`.
- **Foto di Lorenzo.** Manca. In "Chi sono" c'è un segnaposto neutro con le
  istruzioni per sostituirlo (`foto/lorenzo.jpg`). Serve una foto vera: chi lo
  ha appena incontrato in negozio deve riconoscere la faccia. Niente foto di
  repertorio, niente illustrazioni.
- **Le tre pagine in `esempi/` sono ancora nello stile precedente**, non nella
  direzione "dossier tecnico" di `index.html`. È una scelta, non una svista:
  allinearle è un task a parte, da fare solo se Lorenzo lo chiede.
- **Esempi mancanti.** B&B, negozi e studi professionali non hanno ancora un
  template. Nel file c'è un blocco unico marcato `ALTRE CATEGORIE` che trasforma
  il buco in un motivo per scrivere; quando i template esisteranno, si sostituisce
  con altre tre schede.
- Pubblicazione (dominio, repository, hosting) è di Lorenzo e viene dopo.

## Regole di aggiornamento

- Aggiornare questo file solo su richiesta esplicita di Lorenzo.
- Solo pattern durevoli e decisioni che cambierebbero il lavoro di chi arriva
  dopo; non la cronaca di cosa è stato fatto — quella sta nel codice.
- Quando una voce di "In sospeso" si chiude, si rimuove: se ha lasciato una
  regola stabile, quella sale in "Regole che non si negoziano".
- Tenere il file denso: rimuovere ciò che diventa obsoleto invece di accumulare.
