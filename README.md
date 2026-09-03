# HONIORA site — deployment notes

## What's in this package

- `index.html` — the entire site (markup, CSS, and JS all in one file).
- Every image, video, and icon file — hero shots, nav hex buttons, pillar icons, the nav bar wordmark (`honiora-logo.png`), the Mānuka vista banner, the HoniBlog founder photo (`blog-founder-happy-place.jpg`), the HoniBlog Article 02 video still (`blog-kiwi-slimland.jpg`), the HoniBlog Article 03 video still (`blog-jenerise-origins.jpg`), the HoniBlog Article 04 video still (`blog-manuka-benefits.jpg`), and all 14 ingredient photos used in the Stack section (including the new `bifidobacterium_adolescentis.jpg`) — sits flat in the same folder as `index.html`, referenced as plain filenames like `hero-glass.jpg` or `cGP-Pro_blackcurrant.jpg`. There is no `ingredients/` subfolder — everything is one level, beside `index.html`.

## How to host it

This is a static site with no build step. Upload the whole folder as one flat directory — `index.html` and every image/video file beside it, no subfolders. If any image lands in a different folder than `index.html`, or in a subfolder, it will fail to load even though the page itself renders fine, since every image path in the HTML is relative to where `index.html` lives.

For GitHub Pages specifically: commit the folder as-is, flat, to the repo (or the branch/folder GitHub Pages is configured to serve from). Do not nest the images into subfolders or rename files — the HTML references exact filenames.

## Version

This package corresponds to HONIORA_site_v199, updated 2026-09-03.

Recent changes in this version:
- All 14 ingredient-scroll circle photos are now the same visual size. The image frames were already identical, but the actual circle drawn inside each one filled a different amount of that frame (from about 65% up to 98%), so some ingredients looked noticeably bigger than others. Rescaled and recentred every one to a consistent 88% fill. Also squared up thaumatin.jpg, which was 820x786 instead of 820x820, the only one that wasn't a true square file.
- On the lite (mobile) site: the hero glass loop video is 75% bigger (285px tall cap to 499px), and it's now genuinely centred instead of sitting left of centre. The old centring relied on padding that only existed on the right side of its container (reserved for the desktop text column), so this column had nothing balancing it on the left. Fixed by cancelling that reserved space out for this column specifically, and capped the new size responsively so it still centres cleanly without overflowing on narrower phones. Every current iPhone width (375px and up) gets the full 499px.
- The lite (mobile) site now always opens on screen one, the hero. A reload or a shared link with something like #tablet in the URL will no longer land mid-page on a phone. Desktop link behaviour is unchanged.

v198 changes:
- Fixed the real cause of the oversized gap between "HUGE pills and/or chalky, messy powders" and "Every morning?" (and every other line in that hero body text block). It wasn't the line-height on those lines themselves, it was an invisible layout quirk: since only "UPGRADE YOUR RITUAL." is a proper block element, the rest of the paragraph was inheriting that headline's own large 48px/1.15 line spacing as a baseline "strut" for every line, even though the visible text is only 22px. Wrapped that trailing block in its own container with its own font-size and line-height so it no longer borrows the headline's spacing. Line gaps are now the size they were actually styled to be, both lines and paragraph breaks. "HoniOra's Solution:" keeps its original large size, unaffected.

v195 changes:
- Tightened the gap between "UPGRADE YOUR RITUAL." and "HUGE pills and/or chalky, messy powders" in the hero headline. That line break was a block break plus a 6px margin stacked on top, reading as more than one line break. Removed the margin so it's now a single line break, same as the rest of that headline.

v193 changes:
- Tightened the Bifidobacterium adolescentis ingredient-scroll caption: dropped "that survives compression and the effervescent reaction" so it now reads "Microencapsulated live probiotic that ferments the formula's Livaux and Mānuka prebiotic fibres into short-chain fatty acids and supports the gut lining's tight junctions." Also dropped "own" before Livaux.

v192 changes:
- Replaced the Bifidobacterium adolescentis ingredient-scroll photo with the version you sent: a cleaner, sharp-edged circular crop of the same bacteria micrograph, matching the other ingredient tiles' hard-edge circle style more closely than the soft-feathered version used before. Same filename, so no other part of the page needed touching.

v191 changes:
- Corrected D-Allulose back to 110 mg/tab (220 mg/serving). v190 had it at 60 mg, based on a misread of the MBR PDF's table on my part, not an actual formula change. You then sent a clean CSV export of the same Rev 5.7 bill of materials confirming D-Allulose is 110.00 mg/tab, unchanged from Rev 5.6 — corrected on the one site location that carries this figure (stack-matrix table).

v190 changes:
- Formula updated to Rev 5.7 per the new MBR PDF you uploaded (HONIORA_MBR_MakersNutrition_v5.7_140k_38mm.pdf): added Bifidobacterium adolescentis, a microencapsulated probiotic, 50 mg/tab (10 billion CFU per 2-tablet serving). Ingredient count 27→28 everywhere it's stated (hero stat, stat card, Store plan card, AskHoni KB, stack-matrix closing note), unit tablet weight 7,610.00→7,660.00 mg, daily serving 15,220→15,320 mg. Added a new stack-matrix table row, a new AskHoni chat entry, a new item in the hero ingredient list and the header ticker, and a new circular ingredient-scroll photo (you supplied a colourised bacteria micrograph; cropped and soft-edge-masked to match the site's existing circular-photo treatment, same style as the Landkind tile). Science citations independently verified, not taken from your pasted marketing copy: a 2025 human/mouse study (Int J Mol Sci, DOI 10.3390/ijms262412142) on a seafarer cohort showing the species restores gut-lining tight-junction proteins; a 2024 genomic/colitis-model study (Front Microbiol, DOI 10.3389/fmicb.2024.1496280) with the same tight-junction finding plus reduced inflammatory markers; and a 2025 pediatric IBS RCT of a specific strain, PRL2019 (Microorganisms, DOI 10.3390/microorganisms13030627) — flagged on-site as a different strain and a children's population, not a direct match for this product. The "crowds out pathogens" and "second GLP-1 pathway" style claims from your pasted copy were not used as-is since I couldn't independently verify them for this species; the copy instead states the SCFA-fermentation and tight-junction mechanisms that are verified.

**Data flag, still open, please check with Makers Nutrition:** with D-Allulose correctly at 110 mg/tab, summing all 28 per-tablet line items comes to 7,610.00 mg, not the 7,660.00 mg the MBR states as its own header/total-row unit weight — a 50 mg/tab gap. This is the same unresolved gap flagged at Rev 5.6 (it was never about D-Allulose), carried forward unchanged. The site is synced to the stated total, 7,660.00 mg, as the working assumption, same as every revision since Rev 5.6, but this hasn't been confirmed with Makers Nutrition.

v189 changes:
- Rebuilt all four gold nav hex buttons (Reserve Protocol, Reserve Test Tube, Ask Honi, Join List) from scratch: cropped everything outside the dark keyline border away, so the beveled outer band and the leftover shadow blob from the old artwork are gone, leaving a clean tight hexagon with just the border. Added a real soft drop shadow underneath each button (CSS-based, so it sits correctly under the button at all times, not just on hover). Checked at 360px through 1600px, no overflow.

v188 changes:
- Reduced the font size of two lines in the hero sub-copy back down: "HUGE pills and/or chalky, messy powders / Every morning?" and "2 fizzy tablets, 1 glass of water & 60 seconds." are now back to a smaller secondary-text size (16px on desktop, scaling down to 13px on narrow phones). "HoniOra's Solution:" and "UPGRADE YOUR RITUAL." stay large and matched to each other, so the solution line still stands out clearly between the now-smaller surrounding lines. Checked from 360px through 1600px, no overflow.

v187 changes:
- The full four-line sub-copy ("HUGE pills and/or chalky, messy powders / Every morning? / HoniOra's Solution: / 2 fizzy tablets, 1 glass of water & 60 seconds.") is now the same size as "UPGRADE YOUR RITUAL." above it, at every breakpoint (confirmed the computed sizes match exactly). Also tightened the line spacing on that block since a size this large needed less breathing room between lines than the old small-print value. Checked from 360px through 1600px, no overflow.

v186 changes:
- "HoniOra's Solution:" in the hero sub-copy is now the same font size as "MĀNUKA CREATINE PROTOCOL" at every breakpoint (confirmed the computed sizes match exactly, from 15px on narrow phones up to 30px on tablet), so it stands out from the rest of that sentence instead of blending in at the smaller body size. Checked from 360px through 1600px, no overflow or wrapping issues.

v185 changes:
- The line breaks in "HUGE pills and/or chalky, messy powders / Every morning? / HoniOra's Solution: / 2 fizzy tablets, 1 glass of water & 60 seconds." now show everywhere, including desktop. Previously they only showed on mobile/tablet and desktop collapsed it into one flowing paragraph; now the four lines are always visible. Checked at 360px, 390px and 1600px, no overflow.

v184 changes:
- "Upgrade your ritual." is now "UPGRADE YOUR RITUAL." (all caps).
- The sub-copy now capitalizes "Every" ("...powders Every morning?..."), matching the wording you sent. Checked at 360px, 390px, and 1600px, no overflow or wrapping issues.

v183 changes:
- Checked the font on "Upgrade your ritual." against "MĀNUKA CREATINE PROTOCOL": they were already the same family and weight (Arial, bold), computed and confirmed in the browser, so no font change was needed there.
- Increased the size of "Upgrade your ritual.": up to 48px on desktop (was 40px) and up to 42px on mobile/tablet (was 36px), checked from 360px through 1600px wide with no wrapping or overflow issues.
- Updated the hero sub-copy under it to: "HUGE pills and/or chalky, messy powders every morning? HoniOra's Solution: 2 fizzy tablets, 1 glass of water & 60 seconds." (was "HUGE pills and chalky, messy powders every morning? HoniOra's Solution: Two fizzy tablets, a glass of water and sixty seconds."). Kept the same mobile-only line breaks the previous version had (desktop still reads as one flowing paragraph).

v182 changes:
- Replaced the S7 Plant Blend ingredient photo (was a small blue logo graphic, S7.png) with the circular leaf photo you provided (s7_leaf.jpg), sized and framed the same way as the rest of the ingredient grid (820x820, matching the Careflow/Cr-01/cGP-Pro style) instead of the old smaller logo treatment.

v181 changes:
- Fixed a glitch in the matte gold hex buttons from v180: the soft drop-shadow blur baked into the original plaque images had picked up a gold tint when recoloured, showing up as faint gold flecks/streaks in the transparent area around each hex. Rebuilt all four buttons straight from the original source photos with a tight, clean edge, so the transparent background around each hex is genuinely clean now, no flecks, no stray tint.
- Replaced the Careflow Mango Fruit ingredient photo with the new mango-on-mint-circle image you provided, cropped to just the circle and its contents (mango, stem and leaf) with the surrounding white background cut away, matching the tight circular-thumbnail style the other ingredient photos use.

v180 changes:
- All four nav hex buttons (Reserve Protocol, Reserve Test Tube, Ask Honi, Join List) recoloured from white/cream to a flat matte gold. The dark trim line and text stayed as they were for contrast, so the labels are still easy to read. This is a straight recolour of the plaque images themselves (not a CSS filter), applied on both the desktop 4-hex layout and the mobile 2-hex layout, so it's consistent everywhere the buttons appear.
- Checked the spacing between hex 1/2 (Reserve Protocol/Reserve Test Tube) and hex 3/4 (Ask Honi/Join List) on desktop: they were already identical at every width from 1401px up (both pairs use the same tightened gap), so no spacing change was needed there, just confirmed it stayed correct after the recolour.

v179 changes:
- On phones (≤560px), page content now has a wider side margin: 26px, up from 20px. Text blocks, citation lists, ingredient cards and the taste-score table all sit further from the screen edges instead of running close to them. Nothing else changed (the nav bar and hex buttons keep their own separate spacing, untouched by this). Checked from 360px through 1450px, no overflow anywhere.

v178 changes:
- On the mobile nav menu, "Join the Founding List" is now "Join Founding List" (fits on one line at every phone width instead of wrapping).
- Moved "Ask Honi" and "About HoniCo" to the bottom of the RIGHT-hand mobile menu column, after HoniBlog. The left column is now 8 items (Reserve the Protocol through Taste), the right column 8 (2 Tabs through About HoniCo). Checked from 360px through 1000px, no overflow.

v177 changes:
- Moved The Stack, Gut · Heart · Brain, Taste, Ask Honi, and About HoniCo to the bottom of the LEFT-hand column of the mobile menu (previously they'd been placed at the bottom of the right-hand column). The left column is now 10 items, the right column 6. Checked from 360px through 1000px: the longer column still fits comfortably with no overflow.

Recent changes in this version:
- Fixed the hex nav sizing so it actually shows up on vertical (portrait) phones, not just when rotated to landscape. Previously the v175 size increase only applied once the screen got wide enough to enter the "tablet" nav layout, which portrait phones almost never reach, so portrait phones looked unchanged. Now portrait phones get their own two-step growth curve: hexes stay at their existing safe size on the narrowest phones (360-390px, where there's no room to grow without touching the burger icon), then grow meaningfully from 391px up to 560px wide, capping around 106-118px on the widest phones, versus 65px before. Checked from 360px to 560px, no overlap with the burger anywhere.
- Fixed landscape phones getting oversized. Rotating a phone to landscape used to push it past the 560px "phones" width and into the tablet-sized nav (up to 160px hexes, 110px bar), which was far too big for a short landscape screen. Landscape phones (width taller than they are, but under 500px tall) now get their own compact sizing, 70px bar and hexes around 40-43px, similar to portrait. Tablets and desktops in landscape (which have much more height, 600px+) are unaffected and keep the full-size nav. Checked several real phone landscape sizes (iPhone SE through iPhone Pro Max) plus iPad/desktop landscape to confirm the cutoff doesn't catch anything it shouldn't.
- Reordered the right-hand column of the two-column mobile menu: The Stack, Gut · Heart · Brain, Taste, Ask Honi, and About HoniCo now sit together at the bottom of that column, in that order, after the other links (2 Tabs, Ritual, Join the Founding List, Rita Rocks, Lemonwater?, HoniBlog), which keep their previous relative order above them. The left column is unchanged.

v175 changes:
- On the lite (mobile) site, the two hex nav buttons are bigger again on the main lite range (750px-wide and up): the cap is now 160px, up from 138px. On phones (≤560px) they hold at their existing size: tested raising the cap there too, but the vw-driven curve never actually reaches even the old cap within that width range, so there was nothing to gain, and the narrowest phones (360-390px) are already at the physical limit where hex, logo, and burger icon can coexist without touching.
- The nav bar itself is taller again: 110px on the main lite range (up from 92px), 88px on phones (up from 76px), with the hero's top padding and section scroll-offsets adjusted to match so nothing sits under the taller bar.
- The mobile burger slide-out menu is now two columns instead of one long list, so it reads in half the scroll depth. Left column: Reserve the Protocol, Protocol, Mānuka Honey, Science, Function. Right column: everything else, in its previous order (2 Tabs, Ritual, Join the Founding List, Gut · Heart · Brain, The Stack, Rita Rocks, Lemonwater?, Taste, Ask Honi, About HoniCo, HoniBlog). Link targets, colours, and scroll behaviour are unchanged, just the layout.
- The Rita Ora feature photo is now cropped to a 4:3 frame on the lite/mobile and tablet layout (up to 1000px wide): Rita stays fully in view on the left, and the baked-in "HONIORA / Super Star Rita Ora" text stays fully in view, uncropped, top-right. The crop only trims empty background off the left edge of the original photo. Desktop (1001px+) keeps the original full-width photo with the text overlay panel, completely unchanged.
- Checked the whole nav (hex size, bar height) from 360px up through 1450px: no overlap anywhere, no horizontal overflow, logo stays centred, and desktop nav is unaffected.

v174 changes:
- On the lite (mobile) site, the burger slide-out menu list is reordered: "Reserve the Protocol" and "Join the Founding List" (previously near the bottom of the 16-link list) now sit at positions 3 and 4, right after "2 Tabs" and "Ritual". Everything else keeps its previous relative order, just shifted down to make room. Nothing else about the menu (styling, scroll behaviour, link targets) changed.

v173 changes:
- On the lite (mobile) site, the two hex nav buttons ("Reserve Protocol" and "Reserve Test Tube") are up to 50% bigger: 138px on the main lite range (750px-wide screens and up, from 92px) and up to 93px on phones (from 62px, by roughly 800px-wide screens, past the point where phones hand off to the main lite layout). On the narrowest phones (360-430px) they hold close to their existing size, same physical-space tradeoff as previous rounds: the screen just isn't wide enough for a 50%-bigger hex plus the logo plus the burger icon without them touching. Also reduced the gap between the glass video and the "Upgrade your ritual." headline underneath it on the stacked mobile/tablet hero layout, from about 57px down to about 18px. Checked from 360px up through 1400px: no overlap with the logo or burger anywhere, no horizontal overflow, logo stays perfectly centred, and desktop (1401px+) is unchanged.

v172 changes:
- Removed the line break in the "Introducing Jenerise Cr.01" intro paragraph, between "...Olympic athletes in 1992." and "Jenerise Cr-01 Creatine Monohydrate is built to stricter...". It now flows as one continuous paragraph instead of two forced lines.

v171 changes:
- Removed item "03" from the Creatine "What it does" list ("Room for a real creatine dose... Two 38 mm tablets carry it in one dissolve, and twenty-six other named actives besides."). The old item 04 ("Paired with the vascular and gut stack...") is renumbered to 03, so the section now runs 01 through 03 with no gap.

v170 changes:
- Removed item "05" from the Creatine "What it does" list ("Sourced from creatine's own pioneer... Cr-01 comes from Jenerise, founded by Steve Jennings..."). The section now runs 01 through 04. Nothing else in that section changed, and the Jenerise/Steve Jennings sourcing story is still told elsewhere on the page (the Cr-01 ingredient row and the Stack matrix), just not repeated a second time here.

v169 changes:
- On the lite (mobile) site, the nav bar itself is taller (92px, up from 78px on the main lite range; 76px, up from 64px, on phones), the HONIORA wordmark is bigger (58px, up from 48px on the main lite range; 38px, up from 36px, on phones), and the two hex buttons are bigger too (92px, up from 78px on the main lite range; up to 62px, up from 56px, by 500px-wide phones). On the narrowest phones (360-430px) the hexes hold roughly their existing size rather than growing, since the bigger logo now takes up more of the space between it and the burger icon and there just isn't room for both to grow at that width without them touching. Checked from 360px up through 1300px: no overlap with the logo or burger anywhere, no horizontal overflow, logo stays perfectly centred, and desktop (1401px+) is unchanged.

v168 changes:
- The mobile-nav "Reserve Protocol" and "Reserve Test Tube" hexes are bigger again (78px, up from 64px on the main lite range, and up to 56px on phones, from 50px), and a real cascade bug is fixed along the way: the phone-only size and spacing rules were losing to the wider lite-range rules because of a specificity mismatch, so shrinking the hexes down for narrow phones was silently not working. Fixed the selector specificity and re-tuned the phone-width sizing and spacing so the bigger hexes still clear the burger icon and the logo with no overlap and no horizontal overflow, checked from 360px up through 1300px. Also centred the "15,220 mg / 5,000 mg / 15" stats row under the hero on mobile: it used to wrap raggedly, left-aligned, once the layout stacks to one column, now it stacks as one centred group like everything else in that section, on desktop it's unchanged.

v167 changes:
- The mobile nav now puts one hex on each side of the logo (Reserve Protocol on the left, Reserve Test Tube on the right) instead of both together on one side. The logo itself is now always truly centred on the bar (same 1fr/auto/1fr grid technique the desktop nav uses), so it no longer drifts off-centre depending on hex sizing. Also fixed a bug this introduced along the way, where the mobile hexes were briefly showing up as a stray second row underneath the desktop nav above 1400px; that's cleaned up, desktop is back to a single clean row. In "01 / The Ritual" hero copy, added line breaks after "messy powders," "every morning," and "HoniOra's Solution:" on mobile only, desktop keeps the original flowing paragraph. Checked from 360px up through the full lite range and on desktop, no overlap with the logo or burger and no horizontal overflow at any normal phone width.

v166 changes:
- The mobile-nav "Reserve Protocol" and "Reserve Test Tube" hexes are bigger again (64px, 50px on phones, up from 56px/44px) and now sit close beside the logo at every lite/mobile width, not just on narrow phones: they used to be pinned to the screen's left edge, so the gap to the logo grew wider the wider the screen got (up to ~220px on tablet-width "lite" views). They now move as one group with the logo, centred together, so the gap to the logo stays a small, consistent ~20-28px everywhere from 375px up to the 1400px desktop handoff. Checked for overlap against the logo and burger icon at 375, 390, 430, 560, 900 and 1300px, and confirmed the hexes still tap through to the store section.

v165 changes:
- Fixed a real bug in the mobile slide-out menu: the 16-link list is taller than most phone screens, but the menu panel had no scrolling enabled, so it just vertically centred the list and clipped whatever didn't fit, links cut off with no way to reach them. The panel now scrolls properly (tested that every link from "2 Tabs" down to "HoniBlog" is reachable), with room at the top to clear the still-visible header and room at the bottom so the last link isn't flush against the screen edge. Checked on several phone sizes (375, 390, 430px, including a short-screen iPhone SE-sized viewport), no horizontal overflow introduced.

v164 changes:
- The mobile-nav "Reserve Protocol" and "Reserve Test Tube" hexes (added in v163) are bigger and better spaced apart: 40 percent taller (56px, 44px on phones, up from 40px/32px) with real breathing room between them (14px/10px gap, up from a slight overlap). Checked at 375, 390, 430, 900 and 1300px: still clears the centred logo with room to spare and no horizontal overflow.

v163 changes:
- On the mobile (lite) nav, the "Reserve Protocol" and "Reserve Test Tube" hex buttons now sit directly on the nav bar itself, top left, next to the centred logo, instead of only being reachable as a text link inside the slide-out burger menu. Both tap through to the store section. Checked at 375px, 390px, 430px and the wider "lite" widths up to 1400px: no overlap with the logo or burger icon, and no horizontal overflow. The full-size desktop hex buttons above 1400px are unchanged.

v162 changes:
- The "HONIORA" wordmark in the nav bar (`honiora-logo.png`) had a solid white box baked into the image. Its background is now genuinely transparent (proper alpha channel, letters re-matted so there's no white fringe at the edges), so it blends cleanly into the header no matter what's showing behind it as you scroll, instead of showing a hard white rectangle. Checked against several backdrop colours and against the live header in both its transparent and "stuck" (scrolled) states.

v161 changes:
- Ask Honi now gives a targeted answer to "is it safe with blood pressure medication" (and close variants): just the medication/FDA-disclaimer line, instead of the full allergy-and-pregnancy safety paragraph it used to return for any safety-adjacent question. General safety questions (allergies, pregnancy, gluten) still get the full paragraph, which still includes the medication line too. Verified in the browser against several phrasings of both.

v160 changes:
- Added HoniBlog Article 04: "Dr Vicki Petersen: The Powerful Benefits of Mānuka Honey." It's now the top article in the HoniBlog stack (newest first, per the standing rule in the HTML comment above the article list). Same treatment as Articles 02 and 03: a static still from the YouTube Short in a frame the same size as the image, with a play button that opens the video directly on YouTube in a new tab (https://youtube.com/shorts/d7Bky7AMQQw). Checked on desktop, image and link both correct, and the article stack order (04, 03, 02, 01) confirmed.

v159 changes:
- Added HoniBlog Article 03: "Jenerise: Creatine's Origins — Essential for All, Not Just Athletes!" Same treatment as Article 02: a static still from the YouTube Short in a frame the same size as the image, with a play button that opens the video directly on YouTube in a new tab (https://youtube.com/shorts/RnSxf7aFNxA). Checked on desktop, image and link both correct.

v158 changes:
- Fixed a real hero-section layout bug reported on a MacBook Air: at common laptop widths (roughly 1000px to 1600px), the "Upgrade your ritual" copy and the actives list were squeezed into a tiny, wrapped, near-centered column instead of the intended wide left-aligned layout. Root cause was the hero's text block sharing a CSS class with the page's standard side-padding, which was eating width it shouldn't have inside the hero's own layout. Fixing that width alone then exposed a second, previously-hidden problem: with the text column properly widened, the glass image (which is intentionally shifted right to sit close to the copy) started visually overlapping the headline and ingredient list. Both are now fixed together: the text column has its full intended width, and the glass image and text no longer overlap at any desktop width from 1001px up to 2560px+ (spot-checked at 1001, 1280, 1366, 1401, 1440, 1600, 1920, 2560). Also re-checked mobile (375, 390, 430px): type and images are centred as intended and there is no horizontal overflow/side-scroll anywhere on the page.

v156 changes:
- In "05 / The Creatine Dose," the two body paragraphs reworded: "Creatine is one of the most trusted and heavily researched ingredients in wellness and sports nutrition." and "Sourced from creatine's own UK pioneer, Steve Jennings, who first introduced creatine monohydrate to Olympic athletes in 1992. Jenerise Cr-01 Creatine Monohydrate is built to stricter and higher standards than its competitors: independently tested and verified by SGS at 99.96% purity."

v155 changes:
- In "05 / The Creatine Dose," the two paragraphs under the heading ("Creatine is one of the most heavily researched..." and "Sourced from creatine's own pioneer...") are now left-aligned (ragged right edge) instead of centered. The heading above them stays centered. Checked on desktop and mobile, clean.

v154 changes:
- Fixed the "05 / The Creatine Dose" heading from v153: on wider screens (confirmed on an iMac) each of the three intended lines was wrapping again into two, six lines total instead of three, because the heading's normal font size was too large for the line "By the Creatine OG Steve Jennings." to fit on one row. The heading now uses a smaller, dedicated size for this specific three-line heading, so it renders as exactly the three intended lines at every desktop width (checked 1401px to 2560px). On phones the last line still wraps once, since 350px is genuinely too narrow to fit that full phrase at a readable size.

v153 changes:
- In "05 / The Creatine Dose," the heading now reads across three lines: "Introducing Jenerise Cr.01," then "Super Creatine Monohydrate," then "By the Creatine OG Steve Jennings." in gold. Checked on desktop and mobile, no overflow.

v152 changes:
- The "HoniBlog" nav link (desktop nav and mobile menu) now scrolls precisely to "16 / HoniBlog," landing it right at the top of the frame directly under the header, instead of partway down the section.

v151 changes:
- In "01 / The Ritual," the countdown circle's caption now breaks onto two lines: "Seconds to full dissolution" on its own line, "&middot; no stirring" below it.

v150 changes:
- Fixed the Article 02 video: the embedded, autoplay-in-place player from v149 threw YouTube error 153 for this specific video, because its owner has embedding disabled (a setting on the video itself, not something a site can work around). The play button now opens the video directly on YouTube in a new tab instead, which works reliably. Same still image and frame, same play-button look.
- HoniBlog stack reordered: Article 02, "SLIMLAND: Why Kiwis are a GOATED Fruit," now sits first, with Article 01, "Six habits for healthy ageing," below it. Left a note in the code so future articles get added at the top of the stack, newest first, going forward.

v149 changes:
- Added HoniBlog Article 02, "SLIMLAND: Why Kiwis are a GOATED Fruit," directly below Article 01. It shows the supplied still inside a frame sized to match the image, with a play button overlaid. Clicking play swaps the still for an embedded, autoplaying YouTube player (https://youtube.com/shorts/tiKZwCxxdMA) at the exact same frame size, no layout jump. Checked on desktop and mobile, no overflow.

v148 changes:
- The "About HoniCo" nav link (desktop nav and mobile menu) now scrolls precisely to "14 / The Company &middot; About HoniCo.", landing it right at the top of the frame directly under the header, instead of partway down the section.

v147 changes:
- In "03 / M&#257;nuka Honey," the heading now reads "M&#257;nuka honey" on its own line, with "Does far more than sweeten." on the line below in gold. The copy underneath now reads "The 1,000 mg MGO 850+ M&#257;nuka Honey Crystals in HONIORA are a concentrated daily dose of very high MGO goodness, efficient bioactives and significantly reduced honey sugars."

v146 changes:
- The "M&#257;nuka Honey" nav link (desktop nav, mobile menu, and footer) now scrolls precisely to the top of the golden bee mark, instead of landing partway down the section with empty space above it. Verified on desktop: the bee now sits right at the top of the frame, directly under the header, with no lingering gap.

v145 changes:
- In "04 / Look around HoniCo HQ," the embedded VR360 panorama is now 30% taller (300px &rarr; 390px), giving the walkthrough noticeably more room. Checked for overflow/overlap around the frame, clean.

v144 changes:
- In "About HoniCo" &rarr; "Who we are," the closing sentence now stands on its own line in bold: "HoniCo is dedicated to supporting Bees and Apiculture, and we pledge 1% of all profits to Bee welfare and research initiatives." (Fixed a real bug this surfaced along the way: the bold tag was rendering as only medium-weight, not properly bold, because the section's paragraph style set a lighter base weight that the browser's default "bolder" keyword doesn't jump past on its own; fixed by setting the weight explicitly.)

v143 changes:
- In "About HoniCo" &rarr; "02 / Who we are," the bee-mark image replaced with the supplied "1% for the Bees" badge (background made transparent so it sits cleanly on the section's cream background, not as a black box).
- The "Who we are" copy replaced with the new text supplied. The unrelated bee-mark image used in the M&#257;nuka Honey section further up the page was left untouched.

v142 changes:
- The hero stat "27 / Named actives, zero blends" changed to "15 / Full dose Natural actives, Zero blends."

v141 changes:
- "S7® Plant Matrix" added to the bottom of the hero named-actives list, now 12 items.

v140 changes:
- Removed the original 7-item hero claims list ("5g Cr-01 creatine mono...", "Isotonic hydration matrix...", etc). The 11-item named-actives list now sits directly under "Born in New Zealand > Made in USA," where the removed list used to be.

v139 changes:
- The "4D" desktop nav link removed. The "4D" (Gut, heart, brain) section itself is untouched and still reachable via the hero's "Gut, heart, brain" button and the footer link.

v138 changes:
- Tightened the spacing between the two paired hex buttons on each side of the nav (Reserve Protocol/Reserve Test Tube on the left, Ask Honi/Join List on the right), independent of the gap between the hex buttons and the text nav links, which is unchanged. Checked for overflow/overlap at every desktop width from 1401px to 1920px, all clean.

v137 changes:
- "Rita Rocks" moved to the left-hand nav cluster, between Function and Cr.01. "Ritual" moved to the right-hand cluster, between Mānuka Honey and About HoniCo.
- Fixed a real bug this surfaced: with "Rita Rocks" added to the left cluster, its links ran wide enough to overlap the HONIORA logo at 1401px. Fixed by tightening nav link spacing and letter-spacing slightly; checked clean (no overlap, no overflow) from 1401px to 1920px.
- The hero line now reads "HUGE pills and chalky, messy powders every morning?" ("Still swallowing" and "mixing" dropped).

v136 changes:
- "Mānuka Honey" moved to the front of the right-hand nav cluster, now sitting directly beside the logo, between it and "Rita Rocks." Checked for overflow at every desktop width from 1401px to 1920px, all clean.

v135 changes:
- Both hero bullet lists (the original 7-claim list and the new 11-item named-actives list) made bold.

v134 changes:
- The hero copy now reads "Still swallowing HUGE pills and mixing chalky, messy powders every morning?"
- The "2 HONIORA tablets + 300ml cold water + 60 seconds = 27 Named Actives..." line replaced with an 11-item bulleted list of named actives, leading with MGO 850+ Mānuka Honey crystals: Cr-01 Creatine Monohydrate, Livaux® gold kiwi, Feiolix® feijoa, Braincurrant®, cGP-Pro® blackcurrant, VasoDrive-AP® peptide, Careflow® mango, Eriomin® lemon, Landkind® Rhodiola rosea, Thaumatin® Talin. Styled to match the existing claims list right above it.

v133 changes:
- Widened the gap between the hero glass video and the hero text column by 10px. Clean with clear breathing room from 1440px up; at 1401px the text still lightly touches the glass's edge, an improvement over v132 but not fully clear at that one narrow width.

v132 changes:
- The hero text column (Upgrade your ritual, the HONIORA headline, the bullet list, everything in that block) moved left 25px net from where it started this session.

v131 changes:
- The hero glass video (the fizzing tablets in the glass) moved 100px right and 75px down on desktop. Checked for overflow at every desktop width from 1401px to 1920px, all clean; the mobile layout, which already had its own separate centering rule, is unaffected.

v130 changes:
- "4D" moved to the left-hand nav cluster, now the last item, closest to the logo.
- The "HoniCo" desktop nav link renamed to "About HoniCo" (matches the mobile menu's existing wording). Checked for overflow at every desktop width from 1401px to 1920px, all clean.

v129 changes:
- Swapped "Stack" and "Rita Rocks": Stack now sits in the left-hand nav cluster (last item, closest to the logo), Rita Rocks in the right-hand cluster (2nd item, after 4D). Checked for overflow at every desktop width from 1401px to 1920px, all clean.

v128 changes:
- HoniBlog's Article 01 now has the real founder photo (`blog-founder-happy-place.jpg`), cropped to lose the rock on the sand at the bottom, with the caption "HoniOra Founder Greg Miller-Hard in his happy place at the end of his land" overlaid bottom-right on the photo itself (white italic text, drop shadow for legibility), matching how photo captions work elsewhere on the site.
- "Rita Rocks" moved from the right-hand nav cluster to the left, now sitting directly beside the HONIORA logo.
- The 4 hex nav buttons made noticeably bigger again (62px → 82px tall) — moving Rita Rocks left rebalanced the two nav clusters enough to afford the extra size without reintroducing the overflow bug from v127; verified safe at every desktop width from 1401px up to 2560px.

v127 changes:
- Built the HoniBlog section (new "16 / HoniBlog" section): Article 01, "Six habits for healthy ageing." Linked from the nav.
- Fixed a real bug this surfaced: a 6-link nav cluster was overflowing off-screen at normal laptop widths; fixed by tightening nav spacing rather than raising the mobile breakpoint.

v126 changes:
- The 4 hex nav buttons (Reserve Protocol, Reserve Test Tube, Ask Honi, Join the List) each show an info popout on hover/focus.

v125 changes:
- Added a "HoniCo" link to the desktop nav bar (right-hand cluster, after Mānuka Honey), linking to the existing "About HoniCo" section.

v124 changes:
- "Upgrade your ritual." (the lead line above the HONIORA / MĀNUKA CREATINE PROTOCOL headline) made significantly bigger.
- Text updated to: "Upgrade your ritual. Still swallowing giant pills and mixing chalky, messy powders every morning? HoniOra's Solution: Two fizzy tablets, a glass of water and sixty seconds." ("those" dropped from "giant pills").
- On mobile (the lite site), the HONIORA logo in the header is now dead center. Previously it was flex-positioned against the burger menu button using space-between, which pushed it to the left instead of centering it; the burger button is now positioned independently so the logo can sit at true center.

v123 changes:
- The new line above the HONIORA / MĀNUKA CREATINE PROTOCOL headline made bold throughout, with the first sentence set larger than the rest.

v122 changes:
- Reworded the new line above the HONIORA / MĀNUKA CREATINE PROTOCOL headline.

v121 changes:
- Added a new line of copy directly above the HONIORA / MĀNUKA CREATINE PROTOCOL headline.
- Fixed a real, pre-existing mobile bug uncovered while placing that new line: the whole hero text column (headline, tagline, bullet list, everything) was carrying a desktop-only 50px leftward offset that was never reset for mobile, so on phones it sat 50px too far left and clipped content off the left edge. That offset is now cleared on mobile; the desktop layout is unaffected.

v120 changes:
- On the 1st scroll (the auto-scrolling hero ticker), "Balanced Hydration Matrix" moved from last to 2nd position, right after Cr-01 Creatine.

v119 changes:
- Mobile top-nav logo doubled in size (48px, 36px on phones under 560px).
- Fixed the mobile glass video sitting slightly off-center: it was inheriting a 50px rightward offset meant only for the desktop layout, which was never cleared for mobile. Now sits dead center on phones; desktop is unaffected.

v118 changes — reworked the mobile hero, on request for a "lite" mobile layout (built into the same responsive index.html rather than a second file, so there's nothing extra to host):
- Mobile hero order changed: glass video, then the logo/tagline/bullet-list/stats text block, then the Pure Origin pillar leading the other three pillars (Cellular Energy, Vascular Support, Clean Hydration) — previously the pillars sat between the video and the text block.
- Glass video enlarged 50% on mobile (190px → 285px max-height).
- Fixed a real autoplay/loop bug: the script meant to force-start the hero video on browsers that block autoplay was querying a leftover class name (`.glassbox`) that no longer exists anywhere in the page, so that fallback silently did nothing. It now points at the real video element, so the loop reliably starts on phones that need the manual nudge (notably iOS Safari).

v117 changes — a full mobile audit ("is the mobile site screen-width only, and is everything centered"):
- Fixed real horizontal overflow on phones: the four-label "Strength → Gut → Heart → Brain" loop diagram and the ingredient-table group headings ("Effervescent & organoleptic system" etc.) were both set to stay on one line no matter how narrow the screen, so on phones they silently pushed the whole page a few dozen pixels wider than the screen. Both now wrap properly on narrow screens; the page no longer scrolls sideways at any phone width tested (375–430px).
- Fixed a real bug, not just cosmetic: the entire 09 TheStack ingredient table (all 27 actives) was wrapped in a single scroll-reveal animation that only turns visible once 12% of its own height has scrolled into view. That threshold was written for normal-sized blocks — this one block is far taller than any phone screen, so that 12% was mathematically impossible to reach and the whole section stayed invisible on mobile. The reveal now triggers off a small pixel amount instead of a fixed percentage, so it still displays at the same point for every normal-sized block on the page, but now works correctly for this one too.
- Confirmed all page sections and images are properly centered (the `.wrap` container was already using `margin:0 auto`) — the "not centered" feeling was actually the sideways scroll bug above; once that's fixed, everything sits centered as intended.

v116 changes:
- Added a "Cr.01" nav link between Function and the logo, linking to the "Introducing Jenerise Cr.01" creatine section.

v115 changes:
- Nav bar logo enlarged 50% on both desktop and mobile.
- Nav bar spacing widened (the gap between the logo and the hex-button/nav-link clusters on either side) to keep everything comfortably clear at the larger logo size; the breakpoint where the nav collapses to the mobile burger menu moved from 1360px to 1400px so the wider logo always has room before it does.

v114 changes:
- Nav bar wordmark replaced: the "HONIORA" text logo is now the supplied logo image (`honiora-logo.png`), sized to match the previous text logo exactly, on both the desktop-centered and mobile nav bars.
- Hero bullet list and closing line: added missing end-of-line periods for consistent punctuation.

v113 changes:
- Fixed the pinned horizontal-scroll "unit" section (the claims list and the ingredient-photo band): the ingredient images were each triggering a layout refresh the instant they finished loading, and because they load lazily while that section is pinned, those refreshes were firing mid-scroll and causing the scroll position to snap or jump. The unnecessary refreshes are removed; the section now scrubs smoothly start to finish.
- NZ map icon in the Pure Origin pillar enlarged 30% relative to the other three pillar icons.
- 07 Function table reduced in width and centered.
- "No Maltodextrin" removed from the claims list in the pinned scroll section.
- Ask Honi popup: bee logo removed, header shrunk, backdrop-click-to-close confirmed working.
- Fixed the pinned scroll section covering the Mānuka beekeeper banner image below it.
- The two right-column pillar copy blocks (Cellular Energy, Clean Hydration) now range left, matching the left column.
- Ask Honi's Hobbiton answer updated to the latest wording and corrected to the HONI*ORA* brand styling.

Earlier changes:
- Pillar icon images (NZ map, mitochondria, heart, H2O droplet) reverted to their original size after a temporary doubling.
- "4D" nav link moved to the right of the HONIORA logo in the nav bar; nav spacing re-verified across desktop widths.
- Braincurrant® copy in the Stack section rewritten.
- Ingredient images moved out of the `ingredients/` subfolder and flattened into the same folder as `index.html`; all `src` paths updated to match.
