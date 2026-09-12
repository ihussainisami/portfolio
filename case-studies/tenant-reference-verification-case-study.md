<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Tenant Reference Verification &amp; Follow-Up · Case Study</title>
    <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>⚙️</text></svg>" />
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" />
    <link rel="stylesheet" href="../style.css" />
</head>
<body>
    <main class="main" style="max-width:960px; padding-top:20px;">
        <div class="case-study-page">
            <a href="../index.html#projects" class="case-back"><i class="fas fa-arrow-left"></i> Back to Projects</a>

            <h1 class="case-title">Tenant Reference Verification <span>&amp; Follow-Up</span></h1>
            <p class="case-subtitle">An automation that requests tenant references from previous landlords, follows up on its own if they go quiet, and alerts the agent the moment something needs attention, so a reference request never just sits in an inbox.</p>

            <div class="case-block">
                <h3>Tools &amp; <span class="accent">Integrations</span></h3>
                <div class="case-tools">
                    <span class="highlight-tool">n8n</span><span>Google Sheets</span><span>Gmail / SMTP</span>
                    <span>Native n8n Forms</span><span>Schedule Trigger</span>
                </div>
            </div>

            <div class="case-block">
                <h3>The <span class="accent">Business Problem</span></h3>
                <p>Before a lease gets signed, someone has to check the applicant's rental history. That usually means emailing a previous landlord and waiting. In practice, that reply often never comes. The landlord forgets, the email gets buried, or it lands in spam, and there's no system reminding anyone to follow up. The agent ends up manually tracking who has responded and who hasn't, often across several applicants at once, while a move-in date keeps getting closer.</p>
                <div class="matters"><p><strong>Why this matters:</strong> This isn't really a technology problem. It's a follow-up problem, and follow-up is exactly the kind of task that quietly falls apart when it depends on someone remembering to do it.</p></div>
            </div>

            <div class="case-block">
                <h3>Solution <span class="accent">Overview</span></h3>
                <p>The agent submits the applicant's details once, and the system takes over from there. It emails the previous landlord a short reference form, waits for a response, and if nothing comes back within 48 hours, it automatically sends a reminder and alerts the agent at the same time. A separate scheduled check runs quietly in the background as a safety net, so even if something in the main flow gets missed, no case is left unattended. Every step updates a central tracking sheet, so the agent always has one place to check the status of every applicant.</p>
            </div>

            <div class="case-block">
                <h3>Key <span class="accent">Automation Steps</span></h3>
                <ul class="case-steps">
                    <li><span class="num">1</span><span class="step-text"><strong>Intake:</strong> The agent fills out a short form with the applicant's name, the previous landlord's email, their own contact, and the property address. This creates a tracked record and immediately emails the landlord a reference request.</span></li>
                    <li><span class="num">2</span><span class="step-text"><strong>Landlord Response:</strong> The landlord answers five simple yes or no questions, covering rent history, property damage, notice given, and whether they'd rent to the applicant again. Submitting it updates the same tracked record automatically, with no manual entry required.</span></li>
                    <li><span class="num">3</span><span class="step-text"><strong>Automatic Follow-Up:</strong> If the landlord hasn't responded after 48 hours, the system sends them a reminder on its own and notifies the agent at the same time, so nobody is left wondering whether a reference is still pending.</span></li>
                    <li><span class="num">4</span><span class="step-text"><strong>Backup Safety Check:</strong> An hourly background check scans for any case that should have been followed up on but wasn't, catching edge cases the main flow might miss.</span></li>
                </ul>
            </div>

            <div class="case-block">
                <h3>Reliability &amp; <span class="accent">Error Handling</span></h3>
                <div class="case-error-grid">
                    <div class="case-error-item"><i class="fas fa-clock"></i><div class="text"><strong>Follow-Up Never Depends on Memory:</strong> The 48-hour reminder and agent alert fire automatically. Nobody has to remember to check whether a landlord replied.</div></div>
                    <div class="case-error-item"><i class="fas fa-shield-halved"></i><div class="text"><strong>Independent Backup Check:</strong> A separate scheduled workflow re-checks every pending case on its own timer, so a single missed step in the main flow can't let a case fall through unnoticed.</div></div>
                </div>
            </div>

            <div class="case-block">
                <h3>Why This <span class="accent">Matters</span></h3>
                <div class="case-impact"><p>A missed reference check isn't just an inconvenience. It's how agents end up with tenants who have a history of late payments or property damage that nobody caught in time. This system doesn't replace the agent's judgment, it just makes sure the reference request never quietly disappears into an inbox.</p></div>
            </div>

            <div class="case-github-footer" style="display:flex; flex-wrap:wrap; gap:16px;">
                <a href="https://drive.google.com/file/d/19qq3UpHk7mRaThNHkNqWGv2OMTE2qbTl/view?usp=sharing" target="_blank"><i class="fas fa-play"></i> Watch Demo</a>
                <a href="https://github.com/ihussainisami/tenant-reference-verification-automation" target="_blank"><i class="fab fa-github"></i> View Source Code on GitHub</a>
            </div>
        </div>
    </main>
</body>
</html>
