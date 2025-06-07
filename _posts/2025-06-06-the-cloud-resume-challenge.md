---
title: "Cloud Resume Challenge (Azure Edition): With Buttons, Beats, and Budget Cuts"
date: 2025-06-06
categories: [Cybersecurity, Cloud Projects]
tags: [Azure, CI/CD, Resume, Portfolio, Cloudflare, GitHub Actions, Budget Dev, Cloud Resume Challenge]
---

## Project Overview

This was more than just a resume site. It was a full-stack, cloud-native flex with a little extra sauce.

- **Frontend**: Static HTML/CSS resume hosted on Azure Storage.
- **Backend**: Python Azure Function + CosmosDB Table API to track visitors.
- **CI/CD**: GitHub Actions automating backend and frontend deployments.
- **CDN & DNS**: Started with Azure Front Door. Ended up with Cloudflare.
- **Bonus**: A goofy secret "THE BUTTON" feature with music and animations... because why not?

---

## Technical Breakdown

### Infrastructure as Code:
- Provisioned Azure resources using **ARM templates**:
  - Storage Account (with static website hosting)
  - CosmosDB (Table API)
  - Function App
  - Front Door (RIP, we’ll get to that...)

### Frontend Deployment:
- HTML, CSS, and JS dropped into the `$web` container.
- CI/CD with GitHub Actions for hands-free deployment.

### Backend Deployment:
- Python Azure Function connected to CosmosDB to count visitors.
- Separate GitHub Actions workflow deployed the backend.

### DNS + HTTPS:
- Originally routed everything through Azure Front Door to handle HTTPS and custom domains.
- Front Door was linked to the static site origin and DNS was handled via Cloudflare.

### Visitor Counter:
- JavaScript calls the Azure Function and updates the counter live on page load.

---

## Obstacles & Fixes

### CI/CD Confusion:
At first, I thought one GitHub Actions workflow would cover everything. Nope. Needed two—one for the frontend and one for the backend.

### 404 Error Woes:
Azure Static Sites don’t show anything unless you **enable static website hosting** and **upload to the $web container**.

### Permission Denied (Literally):
Ran into Azure permissions issues. Had to scope the service principal carefully just to avoid total chaos.

### Azure Front Door Shenanigans:
Routing wasn’t working because I mistakenly used the storage account root instead of the static website endpoint. Fixed that.

### DNS Propagation Patience:
DNS changes took *forever* to show. Sometimes you just have to wait it out and keep checking `nslookup`.

---

## Bonus Features

- 🎉 **“THE BUTTON”**: Click it and you get a flash of confetti, sound, and a ridiculous AI-generated jingle. Because a resume site doesn’t have to be boring.
- 💼 **Portfolio Button**: Links to my professional portfolio (coming soon).
- 🔥 **Styling & Branding**: Personalized everything with my Grey Key Studios brand in mind.

---

## What I Learned

- The **power of CI/CD**: Once it's set up, pushing changes is butter-smooth.
- Azure's ecosystem can be a tangled mess, but it’s powerful once you get it.
- Debugging cloud infra feels like a boss fight.
- It’s okay to add fun—tech projects are still personal projects.

---

## Addendum 1: “Turn That Shit Off, I’m Poor”

Real talk: After getting everything working, I checked my Azure bill and saw Front Door was eating up my (nonexistent) cloud budget. As cool as global CDN and enterprise-grade routing are, I’m unemployed and not about to pay $7+ a month for a resume site.

So I turned that shit off. Here’s what I did:

- 💸 Deleted Azure Front Door
- 💡 Pointed my custom domain to the Azure static website endpoint using **Cloudflare**
- 🛡️ Free HTTPS, free CDN, and much less drama
- 🔔 Set a $1/month budget alert in Azure because no surprises please

The site still works, it’s still secure, and now it costs literal pennies a month. If you're doing the Cloud Resume Challenge and you're broke like me—**don't be afraid to learn, then pivot.**

---

## Addendum 2: “How I Got My Custom Domain + HTTPS Working (The Cloudflare Worker Saga)”

After wrestling with Azure Front Door, DNS records, and Cloudflare’s orange cloud, I hit the classic wall: **Azure Storage static websites don’t natively support HTTPS for custom domains**—unless you pay for extra services.

### Enter the Cloudflare Worker.

I set up a Worker to proxy all requests from my custom domain to my Azure static website endpoint. Here's how:

- 🧪 Created a dummy A record pointing to `192.0.2.1` and marked it **Proxied**
- 🛠️ Wrote a simple Worker that **fetches** the content from Azure and **returns it** from resume.greykeystudios.com
- 🎉 Boom. Now I get HTTPS + custom domain for free (or close to it)

If you’re stuck with the same Azure + Cloudflare + custom domain headache, **try a Worker**. It’s a little hacky, but it works beautifully.

> #BrokeButCloudy #CloudResumeChallenge #CloudflareWorker

---

More blog posts coming soon—including:
- A deep dive into “THE BUTTON” and the goofy tech behind it
- My birthday post 🎂
- Security projects and portfolio launch

[Stay tuned at blog.greykeystudios.com](https://blog.greykeystudios.com)
