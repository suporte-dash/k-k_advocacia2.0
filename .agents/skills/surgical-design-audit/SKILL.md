---
name: surgical-design-audit
description: Meticulous human-like visual & UX audit across 10 diagnostic lenses. Catches micro-misalignments, redundant text echoes, broken line wraps, visual clutter, CTA competition, cognitive friction, tactile physics, and chromatic monotony that automated linters miss.
when_to_use: "When the user asks to review UI, audit a screenshot or full-page render, find design flaws, check editorial cadence, or spot visual inconsistencies as a human designer would. NOT for automated syntax linting or pure unit testing."
allowed-tools: Read, Grep, Glob
effort: medium
version: 2.0.0
---

# Surgical Design Audit — The Human-Eye UX & Visual Critic (10-Lens Master System)

> "Automated linters verify syntax; the human eye verifies sanity, rhythm, cadence, and harmony."

---

## 🎯 Purpose & Philosophy

Linters, compilers, and test runners cannot see that a badge broke into two lines and ruined a horizontal grid. They cannot feel that repeating the city name twice in 2 centimeters sounds amateurish. They cannot notice that an icon pinned to the top-left leaves an awkward dead space below it, or that four white sections in a row cause visual boredom.

This skill equips the agent with the **Surgical Human Eye**: an uncompromising, empathetic, and aesthetic audit protocol that evaluates interfaces exactly as a Principal Product Designer and Lead UX Engineer would when reviewing actual browser renders.

---

## 👁️ The 10 Human-Eye Diagnostic Lenses

Whenever reviewing a layout, screenshot, or component, inspect systematically across these 10 lenses:

---

### Lens 1: The Cadence & Echo Hunter (Caçador de Ecos e Cacofonia)
*Automated tools check if strings exist. The human eye hears the repetition.*

- **Proximity Echoes:** Search for the exact same word, root, or city/brand name appearing in adjacent lines (e.g., Badge says *"Salinópolis"* and Eyebrow immediately below repeats *"Salinópolis - PA"*).
- **Poetic Cliché Echoes:** Look for metaphorical filler words repeated across sections (e.g., *"escuta"* in the Hero H1 and *"escuta atenta"* in Section 02; *"compromisso"* in the kicker and *"compromisso real"* in the H2).
- **Action-Word Redundancy:** Check if a heading and its sub-lead use the same verb (e.g., *"Análise dedicada para o seu caso"* followed by *"com análise responsável do seu caso"*).
- **Remedy:** Eliminate the echo. Keep the geographic anchor in the badge; focus the kicker on niche authority; change the second instance to tangible verbs (*"diagnóstico"*, *"examinar"*, *"vida laboral"*).

---

### Lens 2: Symmetrical Horizon & Badge Balance (Alinhamento de Grade)
*Linters check if cards render. The human eye notices the broken horizon.*

- **Badge Line-Count Uniformity:** In a 3-column or 2-column card row, do all badges fit on a **single line**? If one card has a 45-character badge that wraps to 2 lines while its neighbors have 15-character badges, the 2-line badge pushes that card's title and content down, destroying the horizontal scanning plane.
- **Title Line-Count Uniformity:** Do titles across parallel cards have roughly the same visual weight (e.g., all 1-2 lines), or does one stretch to 3 lines?
- **Bottom-Action Baseline:** Do all card buttons pin to the absolute bottom via `margin-top: auto` so the row baseline is razor-sharp?
- **Remedy:** Enforce concise, punchy microcopy for badges (`Pesca Artesanal` instead of `★ Tradição Pesqueira em Salinópolis & Costa Norte`). Use `min-height` or flex stretch to lock baselines.

---

### Lens 3: Gravity, Balance & Dead Space (Centro de Gravidade e Simetria)
*Linters see valid flexbox. The human eye sees an unbalanced box.*

- **Top-Pinned Asymmetry:** When an icon box is paired horizontally with text lines (`flex-direction: row; align-items: flex-start;`), if the text has 3 lines, the icon looks orphaned at the top with awkward empty space below it.
- **Symmetrical Posture:** For key contact/metric cards, test if **vertical column centering** (`flex-direction: column; align-items: center; text-align: center;`) with the icon centered on top creates a more prestigious, balanced, and regal posture than a left-pinned list item.
- **Remedy:** Center the icon at the top of the box with a dedicated 44x44px frame, or vertically center the row (`align-items: center`) with a balanced `min-height`.

---

### Lens 4: The Thumb Zone & Mobile Stack Trap (A Lente do Polegar)
*Responsive CSS can pass breakpoints and still be unusable.*

- **The 2-Column Squeeze Trap:** Inspect mobile (360px–390px). Did the Hero or any text-heavy block accidentally render as a 2-column horizontal grid (`grid-template-columns: 1fr 1fr`)? This squeezes text into a 150px column that hyphenates every word.
- **Stacking Priority:** In mobile, always enforce **1 single vertical column** (`flex-direction: column !important;`):
  1. Eyebrow & Headline (100% width, generous typography)
  2. Lead explanation (concise, centered)
  3. Primary conversion CTA (full-width pill, min 48px height)
  4. Visual/Portrait (centered below the buttons, 16px radius, max 340px)
- **Excessive Scroll Fatigue:** If a diagnostic screener or category list has 8+ options, on mobile they must be compacted (shorter paddings, 2-col tight grid) rather than giant cards that require 4 full screen swipes.

---

### Lens 5: CTA Hierarchy & Decision Paralysis (Paz Visual na Conversão)
*Two buttons of equal weight in one card create hesitation.*

- **The Dual-Button Competition:** When a card has both *"Ver detalhes"* and *"Consultar no WhatsApp"*, they must never look identical.
- **The Golden Hierarchy:**
  - **Primary Action (Conversion):** Solid noble accent color (e.g., Deep Wine `#3A171C`), white text, gold micro-accent, prominent shadow.
  - **Secondary Action (Information):** Subtle outlined or translucent pill (e.g., ivory background, 1px champagne border, muted text, file icon).
- **Rule:** The eye must effortlessly know where to click to talk to the professional within 50 milliseconds.

---

### Lens 6: Floating Intrusion & Polish (Invasão de Flutuantes)
*Floating widgets are helpful until they obscure forms, footers, or text.*

- **Floating Greeting Polish:** Floating WhatsApp/chat triggers must never look like unstyled raw boxes. They need:
  - Rounded luxury corners (14px).
  - Avatar of the professionals with an emerald green pulsing "Online" indicator.
  - Micro-tail pointing to the launcher button.
  - Accessible dismiss button ('X') with `sessionStorage` persistence.
- **Mobile Clearance:** Anchor floating widgets at `bottom: calc(4.5rem + env(safe-area-inset-bottom))` with `max-width: calc(100vw - 32px)` so they never bleed off-screen or cover submit buttons.

---

### Lens 7: The Squint Test & Sunlight Contrast (O Teste do Semifechar de Olhos e Luz Solar)
*Mathematical WCAG contrast does not guarantee real-world readability.*

- **The Squint Test:** Semifeche os olhos ao olhar para o layout. Os elementos mais importantes (H1, foto principal, botão de WhatsApp) continuam claramente discerníveis como pontos focais, ou tudo vira uma massa cinzenta homogênea?
- **Gold over Light Pitfall:** Ouro champanhe (`#9E7B56`) é deslumbrante em bordas, ícones e títulos serifados de destaque, mas **ilegível se usado em textos finos de corpo ou parágrafos sobre fundo branco/marfim sob luz solar forte**. O texto de leitura deve ser sempre grafite profundo (`#1E1315` ou `#2B1D20`).
- **Texture Interference:** Texturas de papel ou fundo não podem competir com a tipografia. A opacidade da textura deve permanecer sutil (entre 0.03 e 0.06).

---

### Lens 8: Empathetic Microcopy & Anxiety Relief (Microcopy Humano e Alívio de Ansiedade)
*A interface deve acolher quem está inseguro antes que a dúvida vire abandono.*

- **Anxiety Reducers:** Próximo a qualquer formulário ou CTA de WhatsApp, existe um redutor de ansiedade explícito? (Ex.: *"Atendimento sem compromisso · Sigilo profissional garantido pela OAB"*).
- **Human-Centric Form Labels:** Rótulos de formulário devem soar como um diálogo acolhedor, não um formulário burocrático de repartição pública (ex.: *"Conte brevemente a sua situação"* em vez de *"Descrição do Fato"*).
- **Advisory Empty States:** Se uma busca não retorna resultados (ex.: no FAQ), nunca exiba uma mensagem fria *"Nenhum item encontrado"*. Exiba um **Dossiê Advisory Card**: *"Não encontrou sua dúvida? Cada caso previdenciário tem particularidades únicas. Converse em particular com as advogadas agora mesmo."*

---

### Lens 9: Editorial Rhythm & Chromatic Cadence (Respiração Visual e Ritmo de Revista)
*Monotonia cromática causa cegueira de rolagem.*

- **The Light-Dark Cadence:** Uma página inteira com fundo claro consecutivo cansa o olho. O ritmo nobre intercala seções de respiro claro com blocos de autoridade profunda:
  - `Fundo Papel/Marfim (#FAF6F0)` (Hero)
  - `Fundo Superfície (#FFFFFF)` (Cards de Prova)
  - `Fundo Vinho Nobre (#3A171C)` (Manifesto / Quote)
  - `Fundo Papel (#FAF6F0)` (Serviços)
  - `Fundo Vinho Nobre (#3A171C)` (FAQ Previdenciário)
  - `Fundo Papel (#FAF6F0)` (Atendimento & Mapa)
  - `Fundo Grafite Escuro (#14181D)` (Rodapé Institucional)
- **Visual Pauses:** Cada transição de seção deve ter um espaçamento vertical generoso (80px a 110px no desktop, 54px a 64px no mobile), permitindo que o cérebro processe o bloco antes do próximo estímulo.

---

### Lens 10: Kinetic Touch Physics & Delight (A Física do Toque e Microinterações)
*Interfaces estáticas parecem mortas; interfaces com física parecem orgânicas e responsivas.*

- **Tactile Squish (`:active`):** No toque móvel, botões e cards clicáveis devem oferecer microfeedback háptico visual imediato com leve compressão (`transform: scale(0.97)`), confirmando ao dedo que o toque foi registrado.
- **Directional Energy:** Ícones de seta (`ArrowUpRight`, `ArrowRight`, `ArrowDown`) devem deslizar suavemente de 2px a 3px na direção do fluxo quando o usuário paira o cursor ou toca no link.
- **Cubic-Bezier Easing:** Proibido usar `linear` ou transições mecânicas bruscas. Todas as animações devem usar a curva de aceleração natural de alta costura: `cubic-bezier(0.16, 1, 0.3, 1)`.

---

## 📋 The Surgical Audit Output Protocol

When auditing any interface, output the critique following this mandatory 3-part structure:

### 1. The Unfiltered "What's Broken" Diagnosis
State the exact issues bluntly and without sugarcoating:
- Name the exact component, line, or card.
- Cite the visual friction (e.g., *"The badge wraps to 2 lines, pushing Card 2 down by 28px"*).
- Explain why it damages credibility or conversion.

### 2. The Architectural Rationale (The "Why")
Briefly explain the design and cognitive principle behind the fix (e.g., scanning planes, thumb ergonomics, avoidance of cognitive fatigue).

### 3. The All-in-One Execution Prompt (Single Copy-Paste Block)
Always consolidate ALL fixes into a single, self-contained markdown prompt ready for a builder agent to execute:
- Exact file targets (`src/pages/Home.tsx`, `src/index.css`).
- Exact JSX/TSX replacements.
- Exact CSS blocks with `!important` guards where needed to override stubborn cascades.
- Exact test assertions to update in test files so the CI suite passes.
- Final QA verification commands (`pnpm test`, `tsc --noEmit`, `pnpm run build`).

---

## 🚫 What This Skill Prohibits

- ❌ Never praise a layout passively when visual misalignments, chromatic monotony, or text echoes exist.
- ❌ Never break a working layout on mobile to fix desktop; always test both 360px and 1440px.
- ❌ Never alter canonical client data (OAB numbers, physical addresses, real phone numbers).
- ❌ Never split instructions into multiple fragments when the user needs an all-in-one execution prompt.
