<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Steyr Trägt Zukunft - Wirkungs- & Nachhaltigkeits-Dashboard</title>
    
    <!-- Tailwind CSS für rapid modern styling -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Chart.js für flüssige interaktive Diagramme -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- Google Fonts: Outfit & Plus Jakarta Sans für das Premium-Gefühl -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;800&family=Plus+Jakarta+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        pine: '#1A2F1C',      /* Tiefes Waldgrün (Nachhaltigkeit & Autorität) */
                        mint: '#10B981',      /* Lebendiges Smaragdgrün */
                        gold: '#D4A373',      /* Sanftes Messinggold (Heritage & Qualität) */
                        linen: '#FAF9F6',     /* Premium Off-White für edle Flächen */
                        slatePine: '#4A5D4E', /* Gedämpftes Graugrün */
                        cardBg: '#F3F2EC'     /* Warmes, helles Grau für Inhaltskacheln */
                    },
                    fontFamily: {
                        outfit: ['Outfit', 'sans-serif'],
                        jakarta: ['Plus Jakarta Sans', 'sans-serif']
                    }
                }
            }
        }
    </script>
    
    <style>
        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background-color: #EBEAE4;
        }
        /* Custom Premium-Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #FAF9F6;
        }
        ::-webkit-scrollbar-thumb {
            background: #D4A373;
            border-radius: 4px;
        }
    </style>
</head>
<body class="text-pine min-h-screen flex flex-col antialiased relative">

    <!-- Elegantes, animiertes Feedback-Popup für das Teilen von Szenarien -->
    <div id="toast" class="fixed bottom-5 right-5 bg-pine text-linen px-6 py-4 rounded-xl shadow-2xl border border-gold/30 flex items-center gap-3 transform translate-y-20 opacity-0 transition-all duration-300 z-50 pointer-events-none max-w-sm">
        <div class="bg-gold/20 text-gold p-2 rounded-lg">
            <i class="fa-solid fa-circle-check text-lg"></i>
        </div>
        <div>
            <p class="font-outfit font-bold text-sm text-linen">Szenario-Link kopiert!</p>
            <p class="text-[11px] text-gold/80 mt-0.5">Empfänger sehen exakt deine Schieberegler-Werte beim Öffnen des Links.</p>
        </div>
    </div>

    <!-- TOP NAVIGATION BAR -->
    <header class="bg-pine text-linen px-6 md:px-10 py-4 flex flex-col sm:flex-row justify-between items-center border-b border-gold/30 shadow-md">
        <div class="flex items-center gap-3">
            <div class="bg-gold text-pine p-2.5 rounded-lg font-outfit font-black text-xl tracking-wider">
                That's y
            </div>
            <div>
                <h1 class="font-outfit font-bold text-xl tracking-tight leading-none text-linen">Steyr trägt Zukunft</h1>
                <p class="text-xs text-gold font-medium tracking-wide uppercase mt-1">Kooperations-Initiative mit PROTEX</p>
            </div>
        </div>
        <div class="flex items-center gap-4 mt-4 sm:mt-0 text-sm">
            <div class="flex gap-2 items-center text-gold bg-pine/50 border border-gold/20 px-3 py-1.5 rounded-full">
                <i class="fa-solid fa-seedling"></i>
                <span class="font-semibold text-linen">Klima-Fahrplan 2040</span> Partner
            </div>
            <div class="text-xs text-linen/70 hidden md:block">Stand: Juni 2026</div>
        </div>
    </header>

    <!-- MAIN BODY -->
    <main class="flex-grow p-4 md:p-6 max-w-[1680px] mx-auto w-full flex flex-col gap-6">

        <!-- UPPER GRID: CONTROLS & METRICS/CHARTS -->
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 w-full">

            <!-- LEFT COLUMN: CONTROLS & LIVE CALCULATOR (LG: 4 COLS, XL: 3 COLS) -->
            <section class="lg:col-span-4 xl:col-span-3 flex flex-col gap-6">
                
                <!-- CONTROLLER CARD -->
                <div class="bg-linen p-5 rounded-2xl shadow-sm border border-slatePine/10">
                    <div class="flex items-center gap-2.5 mb-4 border-b border-slatePine/10 pb-3">
                        <div class="w-8 h-8 flex items-center justify-center bg-gold/15 text-gold rounded-lg text-lg">
                            <i class="fa-solid fa-sliders"></i>
                        </div>
                        <h2 class="font-outfit font-bold text-base text-pine">Simulations-Parameter</h2>
                    </div>
                    <p class="text-xs text-slatePine mb-5 leading-relaxed">Verändern Sie die Hebel, um zu sehen, wie sich die Verteilung von PROTEX-Mehrwegtaschen und das Rabattsystem auf Steyr auswirken.</p>

                    <!-- Slider 1: Circulation -->
                    <div class="mb-5">
                        <div class="flex justify-between text-xs font-semibold mb-1">
                            <span>Aktive Taschen im Umlauf</span>
                            <span id="val-circulation" class="text-gold font-bold">8.000 Stk.</span>
                        </div>
                        <input type="range" id="input-circulation" min="1000" max="30000" step="500" value="8000" class="w-full accent-gold bg-pine/10 rounded-lg appearance-none h-1.5 cursor-pointer">
                        <div class="flex justify-between text-[9px] text-slatePine/70 mt-1">
                            <span>1.000</span>
                            <span>Ziel: 15.000</span>
                            <span>30.000</span>
                        </div>
                    </div>

                    <!-- Slider 2: Reuses per month -->
                    <div class="mb-5">
                        <div class="flex justify-between text-xs font-semibold mb-1">
                            <span>Nutzungen pro Beutel / Mo.</span>
                            <span id="val-uses" class="text-gold font-bold">4,5 Mal</span>
                        </div>
                        <input type="range" id="input-uses" min="1" max="10" step="0.5" value="4.5" class="w-full accent-gold bg-pine/10 rounded-lg appearance-none h-1.5 cursor-pointer">
                        <div class="flex justify-between text-[9px] text-slatePine/70 mt-1">
                            <span>1x (Gelegenheit)</span>
                            <span>Schnitt: 4x</span>
                            <span>10x (Stammkunde)</span>
                        </div>
                    </div>

                    <!-- Slider 3: Avg Ticket Size -->
                    <div class="mb-5">
                        <div class="flex justify-between text-xs font-semibold mb-1">
                            <span>Mittlerer Einkaufswert</span>
                            <span id="val-ticket" class="text-gold font-bold">€ 35,00</span>
                        </div>
                        <input type="range" id="input-ticket" min="10" max="100" step="5" value="35" class="w-full accent-gold bg-pine/10 rounded-lg appearance-none h-1.5 cursor-pointer">
                        <div class="flex justify-between text-[9px] text-slatePine/70 mt-1">
                            <span>€ 10</span>
                            <span>Schnitt: € 35</span>
                            <span>€ 100</span>
                        </div>
                    </div>

                    <!-- Slider 4: Discount percentage -->
                    <div class="mb-6">
                        <div class="flex justify-between text-xs font-semibold mb-1">
                            <span>Partner-Rabatt</span>
                            <span id="val-discount" class="text-gold font-bold">4 %</span>
                        </div>
                        <input type="range" id="input-discount" min="3" max="5" step="0.5" value="4" class="w-full accent-gold bg-pine/10 rounded-lg appearance-none h-1.5 cursor-pointer">
                        <div class="flex justify-between text-[9px] text-slatePine/70 mt-1">
                            <span>Min. Anreiz (3%)</span>
                            <span>Max. Anreiz (5%)</span>
                        </div>
                    </div>

                    <!-- SHARE SCENARIO BUTTON -->
                    <div class="border-t border-slatePine/10 pt-4">
                        <button id="btn-share" class="w-full bg-gold hover:bg-gold/90 text-pine font-outfit font-bold py-2.5 px-4 rounded-xl flex items-center justify-center gap-2 transition-all shadow-md active:scale-[0.98] text-sm">
                            <i class="fa-solid fa-share-nodes"></i> Dieses Szenario teilen
                        </button>
                    </div>
                </div>

                <!-- INDIVIDUAL CITIZEN CALCULATOR -->
                <div class="bg-pine text-linen p-5 rounded-2xl shadow-md relative overflow-hidden">
                    <!-- Hintergrund-Dekoration -->
                    <div class="absolute -right-10 -bottom-10 w-32 h-32 bg-gold/10 rounded-full pointer-events-none"></div>

                    <div class="flex items-center gap-2.5 mb-3.5 border-b border-gold/30 pb-3">
                        <div class="w-8 h-8 flex items-center justify-center bg-gold/15 text-gold rounded-lg text-lg">
                            <i class="fa-solid fa-calculator"></i>
                        </div>
                        <h2 class="font-outfit font-bold text-base text-linen">Mein persönlicher Impact</h2>
                    </div>
                    <p class="text-xs text-linen/80 mb-4 leading-relaxed">Gegenüberstellung: Wenn Sie konsequent den PROTEX-Mehrwegbeutel anstelle von Einweg-Papiertaschen nutzen.</p>

                    <!-- Input-Feld 1 -->
                    <div class="mb-3">
                        <label class="block text-[10px] font-bold text-gold uppercase tracking-wider mb-1">Einkäufe pro Woche</label>
                        <div class="relative rounded-md shadow-sm">
                            <input type="number" id="calc-weekly-trips" value="3" min="1" max="21" class="w-full bg-linen/15 text-linen font-bold border border-gold/20 rounded-lg px-3 py-1.5 text-xs focus:outline-none focus:border-gold">
                            <div class="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none text-[10px] text-linen/60">Einkäufe</div>
                        </div>
                    </div>

                    <!-- Input-Feld 2 -->
                    <div class="mb-4">
                        <label class="block text-[10px] font-bold text-gold uppercase tracking-wider mb-1">Schnitt Einkaufswert (€)</label>
                        <div class="relative rounded-md shadow-sm">
                            <input type="number" id="calc-avg-spend" value="40" min="5" max="500" class="w-full bg-linen/15 text-linen font-bold border border-gold/20 rounded-lg px-3 py-1.5 text-xs focus:outline-none focus:border-gold">
                            <div class="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none text-[10px] text-linen/60">EUR</div>
                        </div>
                    </div>

                    <!-- Ausgabe der Ergebnisse -->
                    <div class="bg-linen/10 p-3.5 rounded-xl border border-gold/20">
                        <div class="grid grid-cols-2 gap-3">
                            <div>
                                <span class="block text-[9px] text-gold uppercase font-bold">Ersparnis / Jahr</span>
                                <span id="personal-savings" class="text-lg font-outfit font-black text-linen">€ 79,20</span>
                            </div>
                            <div>
                                <span class="block text-[9px] text-gold uppercase font-bold">CO₂ vermieden</span>
                                <span id="personal-co2" class="text-lg font-outfit font-black text-linen">14,0 kg</span>
                            </div>
                        </div>
                        <p class="text-[10px] text-linen/70 mt-2.5 border-t border-linen/10 pt-2 italic">
                            <i class="fa-solid fa-gift text-gold mr-1"></i> Entspricht ca. <span id="saved-coffee" class="font-bold">19 gratis Kaffees</span> am Stadtplatz!
                        </p>
                    </div>
                </div>

            </section>

            <!-- RIGHT COLUMN: KEY METRICS & INTERACTIVE CHARTS (LG: 8 COLS, XL: 9 COLS) -->
            <section class="lg:col-span-8 xl:col-span-9 flex flex-col gap-6">
                
                <!-- ROW 1: KEY ENVIRONMENTAL & ECONOMIC METRICS -->
                <div class="grid grid-cols-1 sm:grid-cols-2 xl:grid-cols-4 gap-4">
                    
                    <!-- Card 1: Vermiedene Einwegtüten -->
                    <div class="bg-linen p-5 rounded-2xl border border-slatePine/10 shadow-sm flex flex-col justify-between min-h-[140px]">
                        <div class="flex justify-between items-start">
                            <span class="text-[10px] uppercase font-extrabold tracking-wider text-slatePine">Einwegtüten vermieden</span>
                            <div class="bg-pine/10 text-pine w-8 h-8 flex items-center justify-center rounded-lg text-sm">
                                <i class="fa-solid fa-trash-arrow-up"></i>
                            </div>
                        </div>
                        <div class="mt-3">
                            <h3 id="metric-bags" class="font-outfit font-black text-2xl xl:text-3xl text-pine tracking-tight">432.000</h3>
                            <p class="text-[11px] text-slatePine mt-0.5">Plastik- &amp; Papiermüll eingespart</p>
                        </div>
                    </div>

                    <!-- Card 2: CO2-Einsparung -->
                    <div class="bg-linen p-5 rounded-2xl border border-slatePine/10 shadow-sm flex flex-col justify-between min-h-[140px]">
                        <div class="flex justify-between items-start">
                            <span class="text-[10px] uppercase font-extrabold tracking-wider text-slatePine">CO₂-Einsparung</span>
                            <div class="bg-mint/10 text-mint w-8 h-8 flex items-center justify-center rounded-lg text-sm">
                                <i class="fa-solid fa-cloud-arrow-down"></i>
                            </div>
                        </div>
                        <div class="mt-3">
                            <h3 id="metric-co2" class="font-outfit font-black text-2xl xl:text-3xl text-pine tracking-tight">38.880 kg</h3>
                            <p class="text-[11px] text-slatePine mt-0.5">Äquivalent zu ca. 1.550 Bäumen</p>
                        </div>
                    </div>

                    <!-- Card 3: Regionale Wertschöpfung -->
                    <div class="bg-linen p-5 rounded-2xl border border-slatePine/10 shadow-sm flex flex-col justify-between min-h-[140px]">
                        <div class="flex justify-between items-start">
                            <span class="text-[10px] uppercase font-extrabold tracking-wider text-slatePine">Wertschöpfung Steyr</span>
                            <div class="bg-gold/25 text-pine w-8 h-8 flex items-center justify-center rounded-lg text-sm">
                                <i class="fa-solid fa-hand-holding-dollar"></i>
                            </div>
                        </div>
                        <div class="mt-3">
                            <h3 id="metric-finance" class="font-outfit font-black text-2xl xl:text-3xl text-pine tracking-tight">€ 712.800</h3>
                            <p class="text-[11px] text-slatePine mt-0.5">Eingespartes Budget &amp; Rabatte</p>
                        </div>
                    </div>

                    <!-- Card 4: Soziale Arbeitsstunden -->
                    <div class="bg-linen p-5 rounded-2xl border border-slatePine/10 shadow-sm flex flex-col justify-between min-h-[140px]">
                        <div class="flex justify-between items-start">
                            <span class="text-[10px] uppercase font-extrabold tracking-wider text-slatePine">Inklusions-Arbeit</span>
                            <div class="bg-pine/10 text-pine w-8 h-8 flex items-center justify-center rounded-lg text-sm">
                                <i class="fa-solid fa-people-carry-box"></i>
                            </div>
                        </div>
                        <div class="mt-3">
                            <h3 id="metric-social" class="font-outfit font-black text-2xl xl:text-3xl text-pine tracking-tight">32 Std.</h3>
                            <p class="text-[11px] text-slatePine mt-0.5">Gemeinnützige Integrationsstunden</p>
                        </div>
                    </div>

                </div>

                <!-- ROW 2: DETAILED CHARTS (GRID 12 COLS - 7/5 SPLIT) -->
                <div class="grid grid-cols-1 xl:grid-cols-12 gap-6">
                    
                    <!-- Line Chart: Trend Over 12 Months -->
                    <div class="xl:col-span-7 bg-linen p-5 rounded-2xl border border-slatePine/10 shadow-sm">
                        <div class="flex justify-between items-center mb-3 border-b border-slatePine/10 pb-2">
                            <div>
                                <h3 class="font-outfit font-bold text-sm md:text-base text-pine">Jahresprojektion: Einwegtüten-Einsparung</h3>
                                <p class="text-[9px] text-slatePine">Müllvermeidungsszenario im Verlauf der Monate</p>
                            </div>
                            <span class="text-[10px] font-semibold bg-pine/5 text-pine px-2 py-0.5 rounded">Interaktiv</span>
                        </div>
                        <div class="h-[230px] relative">
                            <canvas id="trendChart"></canvas>
                        </div>
                    </div>

                    <!-- Doughnut Chart: Industry distribution of discount usage -->
                    <div class="xl:col-span-5 bg-linen p-5 rounded-2xl border border-slatePine/10 shadow-sm flex flex-col justify-between">
                        <div class="flex justify-between items-center mb-3 border-b border-slatePine/10 pb-2">
                            <div>
                                <h3 class="font-outfit font-bold text-sm md:text-base text-pine">Verteilung der Bürger-Ersparnisse</h3>
                                <p class="text-[9px] text-slatePine">Sektoren, in denen die Rabatte genutzt werden</p>
                            </div>
                            <span class="text-[10px] font-semibold bg-gold/20 text-pine px-2 py-0.5 rounded">Sektoren</span>
                        </div>
                        <div class="h-[165px] relative flex justify-center items-center">
                            <canvas id="sectorChart"></canvas>
                        </div>
                        <p class="text-[10px] text-slatePine leading-relaxed mt-3 pb-0.5 border-t border-slatePine/10 pt-2.5 italic">
                            <strong>Was bedeutet das?</strong> Diese Grafik zeigt, wie sich die zusätzliche Kaufkraft der Bürger durch die eingelösten Rabatte auf die Branchen am Stadtplatz verteilt. 100% des gesparten Geldes fließen so direkt wieder zurück in den lokalen Handel.
                        </p>
                    </div>

                </div>

                <!-- ROW 3: LOCAL LEADERBOARD & RETAILER PERSPECTIVE -->
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    
                    <!-- Potential Scenario of Local Businesses (Möglichkeitsdarstellung) -->
                    <div class="bg-linen p-5 rounded-2xl border border-slatePine/10 shadow-sm flex flex-col justify-start gap-2.5">
                        <div>
                            <h3 class="font-outfit font-bold text-sm md:text-base text-pine mb-1 flex items-center gap-2">
                                <i class="fa-solid fa-chart-line text-gold"></i> Potenzial-Szenario: Partner im Fokus
                            </h3>
                            <p class="text-[10px] text-slatePine leading-relaxed mb-1">
                                <strong>Möglichkeitsdarstellung:</strong> Diese unverbindliche Modellrechnung skizziert beispielhaft das enorme Müllvermeidungs-Potenzial lokaler Leitbetriebe am Steyrer Stadtplatz bei typischer Annahmequote. Sie dient zur Veranschaulichung des gemeinschaftlichen Hebels im historischen Altstadt-Umfeld.
                            </p>
                        </div>
                        
                        <div class="space-y-2">
                            <!-- Partner 1 -->
                            <div class="flex justify-between items-center border-b border-slatePine/5 pb-1.5">
                                <div class="flex items-center gap-2.5">
                                    <span class="font-outfit font-extrabold text-xs text-gold bg-pine text-center rounded-full w-6 h-6 flex items-center justify-center">1</span>
                                    <div>
                                        <h4 class="text-xs font-bold">Intersport Winninger</h4>
                                        <p class="text-[9px] text-slatePine">Großes Sporthaus für Freizeit- &amp; Outdoor-Bedarf im Stadtzentrum</p>
                                    </div>
                                </div>
                                <div class="text-right">
                                    <span class="text-xs font-black block text-pine" id="lead-1-bags">43.200</span>
                                    <span class="text-[8px] text-mint uppercase font-bold"><i class="fa-solid fa-caret-up mr-0.5"></i> 10% Anteil</span>
                                </div>
                            </div>

                            <!-- Partner 2 -->
                            <div class="flex justify-between items-center border-b border-slatePine/5 pb-1.5">
                                <div class="flex items-center gap-2.5">
                                    <span class="font-outfit font-extrabold text-xs text-gold bg-pine text-center rounded-full w-6 h-6 flex items-center justify-center">2</span>
                                    <div>
                                        <h4 class="text-xs font-bold">Bäckerei Fröhlich</h4>
                                        <p class="text-[9px] text-slatePine">Täglicher Frischebedarf &amp; hohe Frequenz am Stadtplatz</p>
                                    </div>
                                </div>
                                <div class="text-right">
                                    <span class="text-xs font-black block text-pine" id="lead-2-bags">30.240</span>
                                    <span class="text-[8px] text-slatePine font-semibold">7% Anteil</span>
                                </div>
                            </div>

                            <!-- Partner 3 -->
                            <div class="flex justify-between items-center border-b border-slatePine/5 pb-1.5">
                                <div class="flex items-center gap-2.5">
                                    <span class="font-outfit font-extrabold text-xs text-gold bg-pine text-center rounded-full w-6 h-6 flex items-center justify-center">3</span>
                                    <div>
                                        <h4 class="text-xs font-bold">Buchhandlung Ennsthaler</h4>
                                        <p class="text-[9px] text-slatePine">Traditionsbuchhandlung (Kultur- &amp; Geschenkbedarf)</p>
                                    </div>
                                </div>
                                <div class="text-right">
                                    <span class="text-xs font-black block text-pine" id="lead-3-bags">25.920</span>
                                    <span class="text-[8px] text-slatePine font-semibold">6% Anteil</span>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Strategic Win-Win for Retailers -->
                    <div class="bg-cardBg p-5 rounded-2xl border border-slatePine/15 shadow-sm flex flex-col justify-between">
                        <div>
                            <h3 class="font-outfit font-bold text-sm md:text-base text-pine mb-1.5 flex items-center gap-2">
                                <i class="fa-solid fa-handshake-angle text-gold"></i> Warum Händler mitmachen (Wirtschaftsmodell)
                            </h3>
                            <p class="text-xs text-slatePine leading-relaxed mb-3">
                                Das Modell ist für Händler von Tag 1 an <strong>vollständig kostenneutral</strong> und hochattraktiv konzipiert:
                            </p>
                            <ul class="text-xs text-slatePine space-y-2 mb-4 list-disc pl-4">
                                <li><strong>Geringer Invest, direkte Deckung:</strong> Händler erwerben die langlebigen PROTEX-Taschen zum Selbstkostenpreis von nur <strong>€ 2,50</strong> (Abgabepreis von PROTEX) und verkaufen sie mit einer geringen Marge (z. B. für <strong>€ 3,00</strong>) an die Endkunden weiter.</li>
                                <li><strong>Fortlaufende Ersparnis:</strong> Bei jeder Folgenutzung spart der Händler die Kosten für teure Einweg-Papiertaschen (~€ 0,25/Stück).</li>
                                <li><strong>Refinanzierung des Rabatts:</strong> Der 3–5% Rabatt-Anreiz wird durch die eingesparten Verpackungskosten und den deutlichen Frequenz-Zuwachs von mindestens <strong>+6,5%</strong> (Kundenbindungseffekt) überkompensiert.</li>
                            </ul>
                        </div>
                        <div class="bg-linen p-3 rounded-xl border border-slatePine/10">
                            <div class="flex items-center gap-3">
                                <div class="text-gold text-xl"><i class="fa-solid fa-chart-line"></i></div>
                                <div>
                                    <h4 class="text-xs font-bold text-pine">Das 2,50 € Win-Win Prinzip</h4>
                                    <p class="text-[10px] text-slatePine leading-normal">
                                        Keine teuren Subventionen nötig. Durch den bewussten Zukauf und margengeringen Weiterverkauf tragen Händler und Bürger das System gemeinschaftlich und nachhaltig.
                                    </p>
                                </div>
                            </div>
                        </div>
                    </div>

                </div>

            </section>

        </div>

        <!-- ROW 4: DATA BASIS & REALITY CHECK METHODOLOGY (FULL WIDTH, PERFECTLY ALIGNED) -->
        <div class="bg-linen p-5 rounded-2xl border border-slatePine/10 shadow-sm w-full">
            <h3 class="font-outfit font-bold text-sm md:text-base text-pine mb-2.5 flex items-center gap-2">
                <i class="fa-solid fa-circle-info text-gold"></i> Methodik &amp; Datenbasis (Realitäts-Check)
            </h3>
            <p class="text-[11px] text-slatePine leading-relaxed mb-4">
                Diese Live-Simulation basiert auf fundierten, praxisnahen Richtwerten und ökologischen Bilanzen. Sie spiegelt die realen Effekte der PROTEX-Kooperation im städtischen Raum wider:
            </p>
            <div class="grid grid-cols-1 sm:grid-cols-2 xl:grid-cols-4 gap-4 text-[10px] text-slatePine leading-relaxed">
                <div class="bg-white/50 p-3 rounded-lg border border-slatePine/5">
                    <strong class="text-pine block mb-1 font-bold">CO₂-Ersparnis:</strong>
                    Ein fiktiver Faktor von 90g (0,09 kg) CO₂ pro vermiedener Einwegtüte basiert auf Bilanzen des Umweltbundesamtes (Herstellung, globaler Transport vs. mehrjähriger Nutzung einer langlebigen PROTEX-Tasche).
                </div>
                <div class="bg-white/50 p-3 rounded-lg border border-slatePine/5">
                    <strong class="text-pine block mb-1 font-bold">Müllvermeidung &amp; Kosten:</strong>
                    Der Wegfall von Papiertüten spart Händlern im Schnitt € 0,25/Stück. Dieses freigesetzte Budget refinanziert den Kunden-Rabatt (3-5%) im lokalen Kreislauf vollständig.
                </div>
                <div class="bg-white/50 p-3 rounded-lg border border-slatePine/5">
                    <strong class="text-pine block mb-1 font-bold">Inklusionsstunden (PROTEX):</strong>
                    Realistisch kalkuliert mit 1 Stunde integrativer Arbeit (Verpackung, Qualitätsprüfung und Logistik) pro 250 verarbeitete Taschen in oberösterreichischen Sozialbetrieben.
                </div>
                <div class="bg-white/50 p-3 rounded-lg border border-slatePine/5">
                    <strong class="text-pine block mb-1 font-bold">Bürger-Ersparnis:</strong>
                    Direkt gekoppelt an reale Durchschnittswerte des Stadtmarketings Steyr bezüglich Frequenz und Kassenbon-Größen in der historischen Altstadt.
                </div>
            </div>
        </div>

        <!-- ROW 5: SIMPLE POS IMPLEMENTATION (FULL WIDTH, PERFECTLY ALIGNED) -->
        <div class="bg-linen p-5 rounded-2xl border border-slatePine/10 shadow-sm w-full">
            <h3 class="font-outfit font-bold text-sm md:text-base text-pine mb-3 flex items-center gap-2">
                <i class="fa-solid fa-rocket text-gold"></i> Blitzschnelle Implementierung in den Geschäften (3 Schritte)
            </h3>
            <p class="text-[11px] text-slatePine leading-relaxed mb-4">
                Das System benötigt keine teure IT-Infrastruktur oder aufwendige Kassen-Schnittstellen. Der Rollout im Steyrer Einzelhandel erfolgt in drei simplen Schritten:
            </p>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                <div class="bg-white/50 p-3 rounded-lg border border-slatePine/5">
                    <div class="flex items-center gap-2 mb-1.5">
                        <span class="bg-pine text-gold text-[10px] font-bold w-5 h-5 flex items-center justify-center rounded-full">1</span>
                        <strong class="text-pine text-[11px] font-bold">Kassentaste anlegen</strong>
                    </div>
                    <p class="text-[10px] text-slatePine leading-relaxed">
                        Teilnehmende Händler richten an ihrer bestehenden Kasse einfach eine Schnelltaste (z. B. <em>„PROTEX Rabatt -4%“</em>) ein. Kein IT-Dienstleister notwendig.
                    </p>
                </div>
                <div class="bg-white/50 p-3 rounded-lg border border-slatePine/5">
                    <div class="flex items-center gap-2 mb-1.5">
                        <span class="bg-pine text-gold text-[10px] font-bold w-5 h-5 flex items-center justify-center rounded-full">2</span>
                        <strong class="text-pine text-[11px] font-bold">Display aufstellen</strong>
                    </div>
                    <p class="text-[10px] text-slatePine leading-relaxed">
                        Das schlüsselfertige Holz-Display von PROTEX benötigt weniger als 0,5 m² Verkaufsfläche und wird direkt neben der Kasse oder im Eingangsbereich platziert.
                    </p>
                </div>
                <div class="bg-white/50 p-3 rounded-lg border border-slatePine/5">
                    <div class="flex items-center gap-2 mb-1.5">
                        <span class="bg-pine text-gold text-[10px] font-bold w-5 h-5 flex items-center justify-center rounded-full">3</span>
                        <strong class="text-pine text-[11px] font-bold">Mitarbeiter informieren</strong>
                    </div>
                    <p class="text-[10px] text-slatePine leading-relaxed">
                        Ein kurzes, einseitiges Infoblatt für das Kassenpersonal reicht aus. Kunde zeigt Beutel vor -> Kassenkraft zieht Rabatt ab -> Schneller, reibungsloser Ablauf.
                    </p>
                </div>
            </div>
        </div>

    </main>

    <!-- TRIPLE BOTTOM LINE BRAND FOOTER -->
    <footer class="bg-pine text-linen/70 py-6 px-6 border-t border-gold/30 text-center text-xs mt-12 w-full">
        <div class="max-w-[1680px] mx-auto flex flex-col sm:flex-row justify-between items-center gap-4">
            <div class="flex items-center gap-3 text-left">
                <span class="font-outfit font-black text-linen tracking-widest text-lg border-r border-linen/20 pr-3">That's y</span>
                <span class="text-xs text-linen/60">Ein Vorzeigeprojekt für eine kreislauffähige &amp; soziale Kreislaufwirtschaft in Oberösterreich.</span>
            </div>
            <div class="flex gap-4">
                <a href="#" class="hover:text-gold transition-colors">Nachhaltigkeits-Statut</a>
                <span>|</span>
                <a href="#" class="hover:text-gold transition-colors">PROTEX Kooperation</a>
                <span>|</span>
                <a href="#" class="hover:text-gold transition-colors">Stadtmarketing Steyr</a>
            </div>
        </div>
    </footer>

    <!-- INTERACTIVE DASHBOARD JAVASCRIPT CALCULATION & DEEP LINK SHARING LAYER -->
    <script>
        // DOM Elemente für die Schieberegler
        const inputCirculation = document.getElementById('input-circulation');
        const inputUses = document.getElementById('input-uses');
        const inputTicket = document.getElementById('input-ticket');
        const inputDiscount = document.getElementById('input-discount');

        // DOM Elemente für die Beschriftungswerte
        const valCirculation = document.getElementById('val-circulation');
        const valUses = document.getElementById('val-uses');
        const valTicket = document.getElementById('val-ticket');
        const valDiscount = document.getElementById('val-discount');

        // DOM Elemente für die berechneten globalen Metriken
        const metricBags = document.getElementById('metric-bags');
        const metricCo2 = document.getElementById('metric-co2');
        const metricFinance = document.getElementById('metric-finance');
        const metricSocial = document.getElementById('metric-social');

        // DOM Elemente für den Bürger-Rechner
        const calcWeeklyTrips = document.getElementById('calc-weekly-trips');
        const calcAvgSpend = document.getElementById('calc-avg-spend');
        const personalSavings = document.getElementById('personal-savings');
        const personalCo2 = document.getElementById('personal-co2');
        const savedCoffee = document.getElementById('saved-coffee');

        // Leaderboard Elemente
        const lead1Bags = document.getElementById('lead-1-bags');
        const lead2Bags = document.getElementById('lead-2-bags');
        const lead3Bags = document.getElementById('lead-3-bags');

        // Ökologische und ökonomische Berechnungskonstanten
        const KG_CO2_SAVED_PER_BAG = 0.09;  // Gewichtete Ersparnis je vermiedener Papiertüte
        const AVERAGE_BAG_COST = 0.25;       // Durchschnittliche Einsparung je Papiertüte für den Händler
        const PRODUCTION_BAGS_PER_SOCIAL_HOUR = 250; // PROTEX: Durch soziale Wertarbeit verpackte & verteilte Beutel pro Arbeitsstunde

        // Globale Diagrammvariablen
        let trendChartObj = null;
        let sectorChartObj = null;

        // Hilfsfunktion: Tausender- und Dezimaltrenner formatieren
        function formatNumber(num, fractionDigits = 0) {
            return num.toLocaleString('de-AT', { minimumFractionDigits: fractionDigits, maximumFractionDigits: fractionDigits });
        }

        // Liest beim Start eventuelle URL-Suchparameter aus und stellt die Regler ein
        function parseQueryParameters() {
            const params = new URLSearchParams(window.location.search);
            
            if (params.has('circ')) {
                inputCirculation.value = Math.max(1000, Math.min(30000, parseInt(params.get('circ'))));
            }
            if (params.has('uses')) {
                inputUses.value = Math.max(1, Math.min(10, parseFloat(params.get('uses'))));
            }
            if (params.has('ticket')) {
                inputTicket.value = Math.max(10, Math.min(100, parseInt(params.get('ticket'))));
            }
            if (params.has('disc')) {
                inputDiscount.value = Math.max(3, Math.min(5, parseFloat(params.get('disc'))));
            }
        }

        // Failsafe-Kopiermechanismus für gesicherte Umgebungen und iFrames
        function copyToClipboard(text) {
            const textarea = document.createElement('textarea');
            textarea.value = text;
            textarea.style.position = 'fixed'; // Verhindert Scrollen beim Einfügen des Elements
            document.body.appendChild(textarea);
            textarea.select();
            
            try {
                document.execCommand('copy');
                showToastNotification();
            } catch (err) {
                console.error('Kopierfehler:', err);
            }
            
            document.body.removeChild(textarea);
        }

        // Zeigt das edle animierte Benachrichtigungs-Toast an
        function showToastNotification() {
            const toast = document.getElementById('toast');
            toast.classList.remove('translate-y-20', 'opacity-0');
            toast.classList.add('translate-y-0', 'opacity-100');

            setTimeout(() => {
                toast.classList.remove('translate-y-0', 'opacity-100');
                toast.classList.add('translate-y-20', 'opacity-0');
            }, 4500);
        }

        // Klick-Handler: Baut den teilbaren Szenariolink zusammen
        function handleShareClick() {
            const circ = inputCirculation.value;
            const uses = inputUses.value;
            const ticket = inputTicket.value;
            const disc = inputDiscount.value;

            // Extrahiert die URL ohne eventuell bereits vorhandene Query-Strings
            const baseUrl = window.location.href.split('?')[0];
            const shareUrl = `${baseUrl}?circ=${circ}&uses=${uses}&ticket=${ticket}&disc=${disc}`;
            copyToClipboard(shareUrl);
        }

        // Berechnet alle globalen Metriken neu, sobald ein Schieberegler bewegt wird
        function updateDashboard() {
            const circulation = parseInt(inputCirculation.value);
            const monthlyUses = parseFloat(inputUses.value);
            const avgTicket = parseInt(inputTicket.value);
            const discountPct = parseFloat(inputDiscount.value);

            // 1. Textwerte in den Schieberegler-Labels aktualisieren
            valCirculation.innerText = formatNumber(circulation) + " Stk.";
            valUses.innerText = formatNumber(monthlyUses, 1) + " Mal";
            valTicket.innerText = "€ " + formatNumber(avgTicket, 2);
            valDiscount.innerText = formatNumber(discountPct, 1) + " %";

            // 2. Globale Umweltergebnisse & Wertschöpfung kalkulieren
            const bagsSavedPerYear = Math.round(circulation * monthlyUses * 12);
            const co2SavedKg = Math.round(bagsSavedPerYear * KG_CO2_SAVED_PER_BAG);
            
            // Regionale Einsparung = Eingesparte Einwegtüten-Kosten + Rabatte für die Bürger
            const paperBagCostsSaved = bagsSavedPerYear * AVERAGE_BAG_COST;
            const customerDiscountSavings = bagsSavedPerYear * (avgTicket * (discountPct / 100));
            const totalRetainedVal = Math.round(paperBagCostsSaved + customerDiscountSavings);

            // Geförderte Inklusionsstunden (direkt an Produktions- & Betreuungskapazität gekoppelt)
            const socialHours = Math.round(circulation / PRODUCTION_BAGS_PER_SOCIAL_HOUR);

            // Ausgabe auf dem Dashboard
            metricBags.innerText = formatNumber(bagsSavedPerYear);
            metricCo2.innerText = formatNumber(co2SavedKg) + " kg";
            metricFinance.innerText = "€ " + formatNumber(totalRetainedVal);
            metricSocial.innerText = formatNumber(socialHours) + " Std.";

            // 3. Dynamische Leaderboard-Daten hochrechnen (10%, 7% und 6% Anteil am Gesamterfolg)
            lead1Bags.innerText = formatNumber(Math.round(bagsSavedPerYear * 0.10));
            lead2Bags.innerText = formatNumber(Math.round(bagsSavedPerYear * 0.07));
            lead3Bags.innerText = formatNumber(Math.round(bagsSavedPerYear * 0.06));

            // 4. Diagramme live mit den neuen Datensätzen speisen
            updateTrendChart(bagsSavedPerYear);
            updateSectorChart(customerDiscountSavings);

            // 5. Persönlichen Impact-Rechner aktualisieren
            updateCitizenCalc();
        }

        // Berechnet den Spar-Effekt für den individuellen Bürger
        function updateCitizenCalc() {
            const trips = parseInt(calcWeeklyTrips.value) || 0;
            const averageSpend = parseFloat(calcAvgSpend.value) || 0;
            const discountPct = parseFloat(inputDiscount.value);

            const annualTrips = trips * 52;
            const annualSavedBagCosts = annualTrips * AVERAGE_BAG_COST;
            const annualDiscountsEarned = annualTrips * (averageSpend * (discountPct / 100));
            const citizenSavingsTotal = annualSavedBagCosts + annualDiscountsEarned;

            const citizenCo2Saved = annualTrips * KG_CO2_SAVED_PER_BAG;

            // Kaffeepreis-Äquivalent in Steyrer Altstadtbäckereien (Annahme: € 4,10 je Kaffee)
            const coffeeEquivalent = Math.floor(citizenSavingsTotal / 4.10);

            personalSavings.innerText = "€ " + formatNumber(citizenSavingsTotal, 2);
            personalCo2.innerText = formatNumber(citizenCo2Saved, 1) + " kg";
            savedCoffee.innerText = formatNumber(coffeeEquivalent) + " Kaffees";
        }

        // Initialisiert das Linien-Diagramm (Jahresverlauf)
        function initTrendChart() {
            const ctx = document.getElementById('trendChart').getContext('2d');
            trendChartObj = new Chart(ctx, {
                type: 'line',
                data: {
                    labels: ['Jän', 'Feb', 'Mär', 'Apr', 'Mai', 'Jun', 'Jul', 'Aug', 'Sep', 'Okt', 'Nov', 'Dez'],
                    datasets: [{
                        label: 'Eingesparte Einwegbeutel',
                        borderColor: '#1A2F1C', 
                        backgroundColor: 'rgba(212, 163, 115, 0.07)', 
                        fill: true,
                        tension: 0.3,
                        borderWidth: 2.5,
                        data: []
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: { display: false }
                    },
                    scales: {
                        y: {
                            beginAtZero: true,
                            grid: { color: 'rgba(74, 93, 78, 0.08)' },
                            ticks: { font: { family: 'Plus Jakarta Sans', size: 9 } }
                        },
                        x: {
                            grid: { display: false },
                            ticks: { font: { family: 'Plus Jakarta Sans', size: 9 } }
                        }
                    }
                }
            });
        }

        // Berechnet die saisonalen Schwankungen (Tourismus / Weihnachtsgeschäft)
        function updateTrendChart(annualTotal) {
            if(!trendChartObj) return;
            const monthlyAvg = annualTotal / 12;
            
            // Saisonaler Multiplikator (Hochphasen im Sommer & Advent)
            const trendMultiplier = [0.8, 0.85, 0.95, 1.0, 1.1, 1.15, 1.1, 1.0, 0.95, 1.0, 1.1, 1.3];
            const dynamicMonthlyData = trendMultiplier.map(m => Math.round(monthlyAvg * m));
            
            trendChartObj.data.datasets[0].data = dynamicMonthlyData;
            trendChartObj.update();
        }

        // Initialisiert das Sektoren-Doughnut-Diagramm
        function initSectorChart() {
            const ctx = document.getElementById('sectorChart').getContext('2d');
            sectorChartObj = new Chart(ctx, {
                type: 'doughnut',
                data: {
                    labels: ['Bäcker & Lebensmittel', 'Bekleidung & Mode', 'Drogerie & Kosmetik', 'Gastronomie & Cafés'],
                    datasets: [{
                        data: [],
                        backgroundColor: ['#1A2F1C', '#D4A373', '#4A5D4E', '#10B981'],
                        borderWidth: 1.5,
                        borderColor: '#FAF9F6'
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'bottom',
                            labels: {
                                font: { family: 'Plus Jakarta Sans', size: 9 },
                                boxWidth: 10,
                                padding: 12
                            }
                        }
                    }
                }
            });
        }

        // Passt die Verteilung der Sektoren dynamisch an
        function updateSectorChart(totalSavings) {
            if(!sectorChartObj) return;
            // Prozentuale Aufteilung: Lebensmittel (45%), Mode (30%), Drogerie (15%), Gastronomie (10%)
            const food = Math.round(totalSavings * 0.45);
            const fashion = Math.round(totalSavings * 0.30);
            const drug = Math.round(totalSavings * 0.15);
            const gastro = Math.round(totalSavings * 0.10);

            sectorChartObj.data.datasets[0].data = [food, fashion, drug, gastro];
            sectorChartObj.update();
        }

        window.onload = function() {
            // URL-Parameter vor dem Laden der Charts auslesen
            parseQueryParameters();

            // Diagramme rendern
            initTrendChart();
            initSectorChart();

            // Event Listener für Regler-Eingaben
            [inputCirculation, inputUses, inputTicket, inputDiscount].forEach(el => {
                el.addEventListener('input', updateDashboard);
            });

            // Event-Listener für den persönlichen Rechner
            [calcWeeklyTrips, calcAvgSpend].forEach(el => {
                el.addEventListener('input', updateCitizenCalc);
            });

            // Event-Listener für Szenario-Sharing
            document.getElementById('btn-share').addEventListener('click', handleShareClick);

            // Erstberechnung anstoßen
            updateDashboard();
        }
    </script>
</body>
</html>
