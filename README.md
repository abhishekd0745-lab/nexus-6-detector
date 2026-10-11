```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#080d1b">
<meta name="description" content="NEXUS 6 is a news analysis prototype that helps users examine claims and understand misinformation signals.">
<title>NEXUS 6 | AI News Intelligence</title>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

:root {
    --bg: #080d1b;
    --panel: #101a2e;
    --border: #263753;
    --cyan: #42e8ff;
    --purple: #9b8cff;
    --text: #f1f5ff;
    --muted: #9baac4;
}

body {
    font-family: Arial, Helvetica, sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    background-image:
        radial-gradient(ellipse at 10% 0%, #12314b55, transparent 45%),
        radial-gradient(ellipse at 90% 30%, #33215a44, transparent 40%);
}

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 22px 7%;
    border-bottom: 1px solid #263753;
    background: #080d1bdd;
    gap: 15px;
    flex-wrap: wrap;
}

.logo {
    font-size: 25px;
    font-weight: 900;
    letter-spacing: 3px;
    color: var(--cyan);
}

.logo span {
    color: white;
}

.status {
    font-size: 12px;
    color: #80f5c2;
    border: 1px solid #276c59;
    padding: 9px 13px;
    border-radius: 30px;
}

main {
    width: min(1050px, 90%);
    margin: 45px auto;
}

.hero {
    text-align: center;
    margin-bottom: 35px;
}

.eyebrow {
    display: inline-block;
    color: var(--cyan);
    font-size: 11px;
    letter-spacing: 3px;
    border: 1px solid #2c6879;
    background: #102b3c;
    border-radius: 30px;
    padding: 9px 15px;
    margin-bottom: 22px;
}

h1 {
    font-size: clamp(36px, 6vw, 65px);
    line-height: 1.1;
    letter-spacing: -2px;
    margin-bottom: 18px;
}

.gradient {
    background: linear-gradient(90deg, var(--cyan), var(--purple));
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
}

.hero p {
    color: var(--muted);
    line-height: 1.8;
    max-width: 640px;
    margin: auto;
    font-size: 15px;
}

.card {
    background: linear-gradient(145deg, #111e34, #0c1425);
    border: 1px solid var(--border);
    border-radius: 20px;
    padding: 28px;
    margin-bottom: 22px;
    box-shadow: 0 15px 50px #0002;
}

.card-heading {
    font-size: 18px;
    margin-bottom: 10px;
}

.subtext {
    color: var(--muted);
    font-size: 13px;
    line-height: 1.7;
    margin-bottom: 20px;
}

label {
    display: block;
    font-size: 13px;
    margin: 20px 0 10px;
    color: #d9e5fb;
}

input, textarea {
    width: 100%;
    background: #080f1e;
    color: white;
    border: 1px solid #2a3c58;
    border-radius: 11px;
    padding: 15px;
    font-family: inherit;
    font-size: 14px;
    outline: none;
}

input:focus, textarea:focus {
    border-color: var(--cyan);
    box-shadow: 0 0 0 3px #42e8ff12;
}

textarea {
    min-height: 170px;
    resize: vertical;
    line-height: 1.7;
}

input::placeholder, textarea::placeholder {
    color: #687995;
}

.actions {
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
    margin-top: 18px;
}

button {
    border: none;
    border-radius: 10px;
    padding: 14px 20px;
    font-size: 13px;
    font-weight: bold;
    cursor: pointer;
    transition: .2s;
}

button:hover {
    transform: translateY(-2px);
}

.primary {
    background: linear-gradient(90deg, var(--cyan), #8ca8ff);
    color: #07111d;
    flex: 1;
    min-width: 180px;
}

.secondary {
    color: #d9e5fb;
    background: #17243a;
    border: 1px solid #344864;
}

.notice {
    color: #91a4c3;
    font-size: 11px;
    line-height: 1.7;
    margin-top: 17px;
}

#results {
    display: none;
}

.result-title {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 12px;
    flex-wrap: wrap;
    margin-bottom: 24px;
}

.badge {
    font-size: 11px;
    border-radius: 20px;
    padding: 8px 12px;
    background: #30284c;
    color: #d0c7ff;
}

.meter-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 15px;
}

.meter {
    background: #0a1323;
    border: 1px solid #263753;
    border-radius: 14px;
    padding: 20px;
}

.meter-label {
    color: var(--muted);
    font-size: 12px;
}

.percent {
    font-size: 34px;
    font-weight: 800;
    margin: 13px 0;
}

.real-color {
    color: #69efb5;
}

.fake-color {
    color: #ff8d9d;
}

.bar {
    height: 7px;
    border-radius: 20px;
    background: #27344b;
    overflow: hidden;
}

.fill {
    height: 100%;
    width: 0;
    border-radius: 20px;
    transition: width .7s;
}

.real-fill {
    background: #69efb5;
}

.fake-fill {
    background: #ff8d9d;
}

.explanation {
    line-height: 1.9;
    color: #c2cee2;
    font-size: 14px;
    white-space: pre-line;
}

.feature-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 15px;
    margin-top: 25px;
}

.feature {
    background: #101a2eaa;
    border: 1px solid var(--border);
    border-radius: 15px;
    padding: 21px;
}

.feature-icon {
    font-size: 25px;
    margin-bottom: 13px;
}

.feature h3 {
    font-size: 14px;
    margin-bottom: 9px;
}

.feature p {
    color: var(--muted);
    font-size: 12px;
    line-height: 1.8;
}

footer {
    text-align: center;
    border-top: 1px solid #263753;
    padding: 28px 15px;
    color: #8393af;
    font-size: 12px;
    line-height: 1.8;
}

footer strong {
    color: var(--cyan);
}

@media(max-width: 650px) {
    header {
        padding: 20px 5%;
    }

    main {
        margin: 30px auto;
    }

    .card {
        padding: 20px;
    }

    .meter-grid, .feature-grid {
        grid-template-columns: 1fr;
    }

    h1 {
        letter-spacing: -1px;
    }
}
</style>
</head>

<body>

<header>
    <div class="logo">NEXUS <span>6</span></div>
    <div class="status">● PROTOTYPE ONLINE</div>
</header>

<main>

<section class="hero">
    <div class="eyebrow">NEWS INTELLIGENCE PLATFORM</div>
    <h1>Truth deserves<br><span class="gradient">better intelligence.</span></h1>
    <p>
        Examine news claims, explore misinformation signals, and understand
        what needs verification with the NEXUS 6 analysis prototype.
    </p>
</section>

<section class="card">
    <h2 class="card-heading">📰 News Analysis</h2>
    <p class="subtext">
        Enter a news headline or article. Add its source or a reference link
        if available to help organize your investigation.
    </p>

    <form id="newsForm">
        <label for="headline">NEWS HEADLINE</label>
        <input id="headline" maxlength="250"
            placeholder="Enter the news headline...">

        <label for="article">ARTICLE TEXT *</label>
        <textarea id="article" maxlength="12000" required
            placeholder="Paste the news article or claim you want to examine..."></textarea>

        <label for="source">SOURCE OR REFERENCE LINK (OPTIONAL)</label>
        <input id="source" maxlength="500"
            placeholder="Publication name or article link">

        <div class="actions">
            <button class="primary" id="analyzeButton" type="submit">
                ✦ ANALYZE NEWS
            </button>
            <button class="secondary" type="button" id="exampleButton">
                TRY EXAMPLE
            </button>
            <button class="secondary" type="button" id="clearButton">
                CLEAR
            </button>
        </div>
    </form>

    <p class="notice">
        Important: This free prototype uses illustrative text-based signals.
        It does not connect to a verified news database or an AI service.
        Its results cannot establish whether a story is true or false.
    </p>
</section>

<section id="results" aria-live="polite">
    <div class="card">
        <div class="result-title">
            <h2>Analysis Dashboard</h2>
            <span class="badge">PRELIMINARY SCREENING</span>
        </div>

        <p class="subtext" id="summary"></p>

        <div class="meter-grid">
            <div class="meter">
                <div class="meter-label">VERIFICATION SIGNAL</div>
                <div class="percent real-color" id="realPercent">--%</div>
                <div class="bar">
                    <div class="fill real-fill" id="realBar"></div>
                </div>
            </div>

            <div class="meter">
                <div class="meter-label">CAUTION SIGNAL</div>
                <div class="percent fake-color" id="fakePercent">--%</div>
                <div class="bar">
                    <div class="fill fake-fill" id="fakeBar"></div>
                </div>
            </div>
        </div>

        <p class="notice">
            These percentages represent heuristic screening signals, NOT
            the probability that an article is real or fake.
        </p>
    </div>

    <div class="card">
        <h2 class="card-heading">🤖 Analysis Explanation</h2>
        <p class="subtext">
            Here are the language patterns found in the submitted text.
            They are clues to investigate, not proof of misinformation.
        </p>
        <div class="explanation" id="explanation"></div>
    </div>

    <div class="card">
        <h2 class="card-heading">🔎 Recommended Verification Steps</h2>
        <div class="explanation" id="recommendations"></div>
    </div>
</section>

<section class="feature-grid">
    <div class="feature">
        <div class="feature-icon">🧠</div>
        <h3>Text Screening</h3>
        <p>Highlights selected language patterns that may deserve a closer look.</p>
    </div>

    <div class="feature">
        <div class="feature-icon">📊</div>
        <h3>Visual Dashboard</h3>
        <p>Displays screening signals in a simple, readable interface.</p>
    </div>

    <div class="feature">
        <div class="feature-icon">🛡️</div>
        <h3>Think Critically</h3>
        <p>Encourages source checks and evidence-based news evaluation.</p>
    </div>
</section>

</main>

<footer>
    <strong>NEXUS 6</strong> · AI News Intelligence Prototype<br>
    Built for responsible information analysis.<br>
    Screening signals are not fact-checks or confirmed AI predictions.
</footer>

<script>
const form = document.getElementById("newsForm");
const articleInput = document.getElementById("article");
const headlineInput = document.getElementById("headline");
const sourceInput = document.getElementById("source");
const results = document.getElementById("results");

document.getElementById("exampleButton").addEventListener("click", () => {
    headlineInput.value = "Example: A major discovery is announced";
    articleInput.value =
        "A report claims that researchers have announced a major discovery. " +
        "The article does not identify the research team, link to a published " +
        "study, or name an independent source. Readers should check the original " +
        "research and look for confirmation from reputable publications.";
    sourceInput.value = "";
    articleInput.focus();
});

document.getElementById("clearButton").addEventListener("click", () => {
    form.reset();
    results.style.display = "none";
    document.getElementById("realBar").style.width = "0";
    document.getElementById("fakeBar").style.width = "0";
});

form.addEventListener("submit", (event) => {
    event.preventDefault();

    const text = articleInput.value.trim();
    const headline = headlineInput.value.trim();
    const source = sourceInput.value.trim();

    if (text.length < 20) {
        alert("Please enter at least 20 characters of article text.");
        return;
    }

    const combined = (headline + " " + text).toLowerCase();

    const warningPhrases = [
        "shocking", "you won't believe", "secret they hide",
        "share immediately", "forward this", "wake up",
        "100% guaranteed", "miracle cure", "breaking!!!",
        "everyone is hiding", "before it gets deleted"
    ];

    const cautiousPhrases = [
        "according to the study", "published in",
        "peer-reviewed", "official report", "researchers found",
        "data shows", "the report states", "according to"
    ];

    const warningMatches = warningPhrases.filter(
        phrase => combined.includes(phrase)
    );

    const cautiousMatches = cautiousPhrases.filter(
        phrase => combined.includes(phrase)
    );

    const hasSource = source.length > 0;
    const hasNumbers = /\b\d+([.,]\d+)?%?\b/.test(text);
    const hasDate = /\b(19|20)\d{2}\b/.test(text);
    const wordCount = text.split(/\s+/).filter(Boolean).length;

    let caution = 35;
    caution += warningMatches.length * 10;
    caution -= cautiousMatches.length * 5;
    caution -= hasSource ? 5 : 0;
    caution += wordCount < 40 ? 5 : 0;
    caution = Math.max(10, Math.min(90, caution));

    const verification = 100 - caution;

    document.getElementById("realPercent").textContent =
        verification + "%";
    document.getElementById("fakePercent").textContent =
        caution + "%";

    document.getElementById("realBar").style.width =
        verification + "%";
    document.getElementById("fakeBar").style.width =
        caution + "%";

    document.getElementById("summary").textContent =
        "Text length: " + wordCount + " words. " +
        "This is an initial language-pattern screening, not a verdict " +
        "on the accuracy of the claim.";

    let explanation = [];

    if (warningMatches.length) {
        explanation.push(
            "Potentially sensational wording detected: " +
            warningMatches.join(", ") + ". Such wording may be used " +
            "to attract attention, but does not prove a claim is false."
        );
    } else {
        explanation.push(
            "No phrases from the prototype's limited sensational-language " +
            "list were detected. This does not mean the claim is accurate."
        );
    }

    if (cautiousMatches.length) {
        explanation.push(
            "Reference-style phrases detected: " +
            cautiousMatches.join(", ") +
            ". Open the original study or report to verify the context."
        );
    } else {
        explanation.push(
            "The selected reference-style phrases were not detected. " +
            "Check whether the article names its sources and provides " +
            "links to original evidence."
        );
    }

    explanation.push(
        "A year " + (hasDate ? "was" : "was not") +
        " detected. A number " + (hasNumbers ? "was" : "was not") +
        " detected. Numbers and dates require independent verification."
    );

    explanation.push(
        "A source or reference " +
        (hasSource ? "was supplied" : "was not supplied") +
        ". Supplying a link does not establish that its contents are reliable."
    );

    document.getElementById("explanation").textContent =
        explanation.join("\n\n");

    document.getElementById("recommendations").textContent =
        "1. Find the original source of the claim.\n\n" +
        "2. Check whether reputable, independent news organizations " +
        "report the same facts.\n\n" +
        "3. Look for official records, original research, and full context.\n\n" +
        "4. Check the publication date and whether images or quotations " +
        "have been taken out of context.\n\n" +
        "5. Do not share a serious claim until you have checked the evidence.";

    results.style.display = "block";
    results.scrollIntoView({ behavior: "smooth", block: "start" });
});
</script>

</body>
</html>
```
