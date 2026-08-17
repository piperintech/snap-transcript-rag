# SNAP Transcript RAG Tool — For INAZA Integration

**To: INAZA Delivery Team**  
**From: Manu (Manuela Gonzalez), Operations & Technology, SNAP Insurance Service LLC**

---

## What This Is

A **bilingual (English/Spanish) transcript translator and claim summarizer** that uses Claude AI + RAG (Retrieval-Augmented Generation) to:

1. **Translate** call transcripts with SNAP insurance terminology
2. **Summarize** claims in two formats:
   - **MT Entry** (ultra-compact, 1-3 sentences, ALL CAPS) → feeds into MODOTECH
   - **Claims Summary** (detailed, professional narrative) → for adjuster review
3. **Learn** from patterns — grows smarter with every claim type we see

---

## Why This Matters for Your Underwriting Integration

### Current Workflow (Manual)
Lucy Bot (voice) → Raw transcript → Manual translation → Manual FNOL entry → MODOTECH

### With This Tool
Lucy Bot (voice) → Raw transcript → **Auto-translate + MT Entry generation** → MODOTECH  
(Fewer manual steps, faster claims entry, consistent terminology)

### Integration Point
This tool can feed into your **underwriting automation flow** by:
- Pre-cleaning and standardizing claim descriptions
- Extracting key details (location, vehicles, liability indicators)
- Flagging anomalies (uninsured, border incidents, multi-vehicle)
- Providing structured data for your decision engine

---

## Try It Live

**Translator:** https://snap-transcript-rag-xxx.netlify.app/snap-transcript-rag.html

**Steps:**
1. Paste a Spanish claim call transcript (or English for demo)
2. Click **"Process"**
3. See: Translation
4. Click **"MT Entry"** tab → **"Generate"** → ultra-compact MODOTECH format
5. Click **"Claims Summary"** tab → **"Generate"** → professional narrative

**Example Spanish Transcript:**
```
Yo estaba en la calle haciendo unas vueltas para mis hijos y cuando estaba 
llegando a mi casa en 2600 lakefront tcl, fui a voltear a la izquierda y 
un carro venía en contracheque y me pegó de frente. El tipo no me quiso 
decir cuál era su aseguranza, pero cogí la placa del carro que era 1289 y 
un ford 150. No supe qué hacer así que ojela ustedes me puedan ayudar.
```

**Expected MT Entry:**
```
IV TURNING LEFT INTO CV (FORD 150, PLATE 1289) AT 2600 LAKEFRONT TCL. 
HEAD-ON COLLISION. CV DRIVER REFUSED TO PROVIDE INS INFO.
```

**Expected Claims Summary:**
```
Insured was turning left onto 2600 Lakefront TCL when a Ford 150 (plate 1289) 
traveling in the opposite direction struck the insured's vehicle head-on. The 
other driver refused to provide insurance information. No injuries reported at 
time of call.
```

---

## Technical Details

**Built With:**
- Claude API (Anthropic) for translation + summarization
- RAG (knowledge base) with 15+ SNAP insurance abbreviations, 8+ incident patterns
- Netlify serverless function for secure API proxy
- GitHub + Netlify for hosting (no infrastructure costs)

**SNAP Knowledge Base Includes:**
- Core abbreviations: IV, CV, R/E, CLMT, INSD, PSGR, PKG LOT, APTS, UNINS, SUBR, etc.
- Incident types: Rear-end, parking lot, hit-and-run, intersection, border, rental vehicles
- MT Entry patterns: Ultra-compact format examples for each type
- Manu's voice + SNAP professional tone: Consistent, direct, adjuster-first

**Data:** All processing stays between SNAP, Netlify, and Anthropic. No third-party storage.

---

## Next Steps for Integration

### Phase 1: Feedback (This Month)
- You test the translator with real claim transcripts
- Give us feedback on translation quality, MT formatting, any patterns we're missing
- We refine the knowledge base

### Phase 2: Lucy Bot Integration (Next Quarter)
- Lucy captures call → feeds into this tool automatically
- Tool generates clean MT Entry → pre-fills MODOTECH claim creation
- Reduces manual entry time per claim by ~70%

### Phase 3: Your Underwriting Automation (Future)
- Structured outputs from this tool feed into your decision engine
- You leverage clean translations + flagged anomalies for triage
- Faster underwriting turnaround

---

## Questions?

- **Translation accuracy:** Does the tool capture claims correctly?
- **MT format:** Are the compact summaries what you'd send to MODOTECH?
- **Integration:** How would you want to receive the data? (API, CSV export, direct MODOTECH sync?)
- **Terminology:** Any SNAP-specific language we should add to the knowledge base?

---

## Access

**Translator:** https://snap-transcript-rag-xxx.netlify.app/snap-transcript-rag.html  
**KB Manager:** https://snap-transcript-rag-xxx.netlify.app/snap-kb-manager.html (internal only)  
**GitHub Repo:** https://github.com/piperintech/snap-transcript-rag (source code, full transparency)

---

**Built by Manu for SNAP. Let's make claims faster, smarter, and more consistent.**
