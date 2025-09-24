# Phishing Email Analysis — sample-email-You’re-Shortlisted.eml
Date: 2025-09-19
Analyst: <Your Name>
Source file: You’re Shortlisted – Cyber Security Internship First Selection Round 🚀.eml.

## Summary
Conclusion: **Likely legitimate marketing/recruitment email sent via Sendinblue on behalf of Dharmakit Networks**, but verify before clicking scheduling links. Evidence: SPF/DKIM/DMARC all **pass** for the sending chain; links are Sendinblue redirect/tracking URLs rather than direct attacker domains. However — treat unknown senders with caution: confirm using the employer’s official site or contact HR directly before sharing sensitive info.

## Key findings (evidence lines and explanation)
1. **From header (display + envelope)**  
   - Display: `HR Team <hr@dharmakit.com>` (header.from).  
   - Return-Path/envelope-from: `bounces-haeu5-hr=dharmakit.com@ke.d.sender-sib.com` — indicates the message was sent via a mailing provider (Sendinblue / sender-sib).

2. **Authentication (SPF / DKIM / DMARC) — high-trust indicators**  
   - `Authentication-Results` shows: `dkim=pass` (for `dharmakit.com` and `mailin.fr`), `spf=pass` for the sending IP `77.32.148.109`, and `dmarc=pass`. These results strongly indicate the message is legitimately sent via the configured mailing service for `dharmakit.com`.

3. **Received chain / origin IP**  
   - `Received` from `ke.d.sender-sib.com` (IP `77.32.148.109`). This matches Sendinblue infrastructure (a legitimate mass-mailing provider). Example header line: `Received: from ke.d.sender-sib.com ... [77.32.148.109]`.

4. **Message body & links**  
   - The email contains scheduling links and image links that use Sendinblue tracking domains, e.g. `https://haeu5.r.ag.d.sendibm3.com/mk/cl/f/sh/...` (these are redirect/tracking URLs hosted by the mailing provider). The visible CTA text is `Schedule Interview`.  
   - Because links are tracking/redirect links, prefer to: (a) verify the target by expanding the redirect (or hover to view destination), or (b) visit the official Dharmakit website manually and locate the interview scheduling there.

5. **Personalization**  
   - The body addresses you by name: `Hi mankamuthaka soma niranjan,` — personalization is consistent with legitimate recruitment mailings (but personalization alone is not definitive).

6. **Mailing metadata**  
   - X-Mailer / Campaign fields indicate a mail campaign: `X-Mailer: Sendinblue`, `X-Mailin-Campaign: 19` — consistent with legitimate marketing/recruiting campaigns.

## Risk assessment (overall)
- **Risk level:** Low-to-Moderate (operational).  
  - Authentication checks pass (lowers phishing risk).  
  - Redirect/tracking links mean clicking directly could still be risky if the final landing page is malicious — verify landing host before entering any credentials.  
  - If you did not apply to or expect contact from Dharmakit Networks, treat as suspicious until verified.

## Recommended actions (what to do next)
1. **Do not click** the CTA from your primary machine if you’re unsure. Instead:
   - Hover the link to see the destination. Or copy the `href` and use an URL-expansion / preview tool to see final redirect target.  
   - If comfortable, open the final target in a sandbox or ephemeral browser session.
2. **Verify independently**:
   - Go to `dharmakit.com` (type the URL manually) and check for any official recruitment notices or career portal.  
   - Or contact Dharmakit HR directly via a verified phone/email from their official website (do not use the contact links inside the email until verified).
3. **If you applied or expected this**: it is reasonable to schedule through the provided link, but prefer manual verification first.
4. **If you did not expect it**: mark as suspicious and optionally report to your security team (if this is a work address) or ignore/unsubscribe.
5. **Archive evidence**: keep the raw headers and save screenshots of the Authentication-Results & Received chain for future reference.

## Appendix — select raw header snippets (copied for evidence)
Below are the actual header lines copied verbatim from the uploaded .eml for reproducibility and evidence.

```
Delivered-To: msniranjan2004@gmail.com
Received: by 2002:a54:2b86:0:b0:2ac:a1eb:e109 with SMTP id f6csp368294ecp;
        Fri, 19 Sep 2025 11:38:23 -0700 (PDT)
X-Google-Smtp-Source: AGHT+IHZNnxMucYlQT1ZWFG6Wc+QEaViuqibCjKRqbhM3hcEHAyQf3fS6rR3sGYJWnMt+Y9e9UyX
X-Received: by 2002:a17:903:124a:b0:262:d081:96c with SMTP id d9443c01a7336-269ba441ba2mr62461335ad.17.1758307102989;
        Fri, 19 Sep 2025 11:38:22 -0700 (PDT)
ARC-Seal: i=1; a=rsa-sha256; t=1758307102; cv=none;
        d=google.com; s=arc-20240605;
        b=Sw+Tmq9YdN1KfhvTjKrgp9Pd1APY8j3fzxTwHUrmtSw27BdP7F/vjBxJVGj1212mLe
         gphKoiZg0WmGRFsnC6fFzE7wSX2Lt7c0rrbMudxjh5yJgQXnY5szu5Ftri1NUO2x/cYl
         lxRPXZ2ws/nAEvTmBaOYioh/IU+uln9e+cli7BkomZL1IWDQ5WnlFCHfrAIh/lCK4xPe
         z0SLCzQP5+jELY4ZQhacon0Uj9ZsfhKWotHWloz04P84prl+irNtS6oxP9vW1lGmxEp+
         zFEo8RX2r5BJQpGqjL0als3nGp8UQcx2cIXOkedcGSgYrk6YEiOoTzTURodD3H7uZti1
         WzFA==
ARC-Message-Signature: i=1; a=rsa-sha256; c=relaxed/relaxed; d=google.com; s=arc-20240605;
        h=reply-to:message-id:mime-version:list-unsubscribe-post
         :list-unsubscribe:list-id:from:feedback-id:date:subject:to
         :dkim-signature:dkim-signature;
        bh=wawEiJc9Co8g3WO2EwhKV6UrOiazJRard4+eZRWvegE=;
        fh=0/SZ2cCStrOenlisRr1JEokRwaYWHHsb5cWeRFJP3uU=;
        b=FbliHSWIrLnNZuk0ouWHYyGUNBDcLXUbKnw7U4fsrQXVJ2Olb4tewhGL4pDFp7VqHJ
         tOhV1/PxEHpPyGJX6+9pF/AbmpIzlV/hemvEFJzdcS1DW2FoJjdT29XfrRIrPhXLexXd
         B757VEJH8TXfeivggjp9pf186vpnZsQ4ZcKGohtshX3b7l2U5bqRgc2HvUKz2zwxavwy
         AfwQkNS2ZA8oil2IeP2K/Q1KwkipH84RVQZm/5dR7EEgDJWqseaH2w3nUDv2fZHqhssG
         gcb+wwwz6bfQIS1m/AgGH7/EOfz4q9gbLd7WcRUKgEfBq9z7nTM634leG+U4wycQVToe
         dWbA==;
        dara=google.com
ARC-Authentication-Results: i=1; mx.google.com;
       dkim=pass header.i=@dharmakit.com header.s=brevo2 header.b=qCvIdkY0;
       dkim=pass header.i=@mailin.fr header.s=mail header.b=iwbSZ06B;
       spf=pass (google.com: domain of bounces-haeu5-hr=dharmakit.com@ke.d.sender-sib.com designates 77.32.148.109 as permitted sender) smtp.mailfrom="bounces-haeu5-hr=dharmakit.com@ke.d.sender-sib.com";
       dmarc=pass (p=REJECT sp=REJECT dis=NONE) header.from=dharmakit.com
Return-Path: <bounces-haeu5-hr=dharmakit.com@ke.d.sender-sib.com>
Received: from ke.d.sender-sib.com (ke.d.sender-sib.com. [77.32.148.109])
        by mx.google.com with ESMTPS id d9443c01a7336-26980328301si46304345ad.739.2025.09.19.11.38.21
        for <msniranjan2004@gmail.com>
        (version=TLS1_3 cipher=TLS_AES_256_GCM_SHA384 bits=256/256);
        Fri, 19 Sep 2025 11:38:22 -0700 (PDT)
Received-SPF: pass (google.com: domain of bounces-haeu5-hr=dharmakit.com@ke.d.sender-sib.com designates 77.32.148.109 as permitted sender) client-ip=77.32.148.109;
Authentication-Results: mx.google.com;
       dkim=pass header.i=@dharmakit.com header.s=brevo2 header.b=qCvIdkY0;
       dkim=pass header.i=@mailin.fr header.s=mail header.b=iwbSZ06B;
       spf=pass (google.com: domain of bounces-haeu5-hr=dharmakit.com@ke.d.sender-sib.com designates 77.32.148.109 as permitted sender) smtp.mailfrom="bounces-haeu5-hr=dharmakit.com@ke.d.sender-sib.com";
       dmarc=pass (p=REJECT sp=REJECT dis=NONE) header.from=dharmakit.com
DKIM-Signature: a=rsa-sha256; bh=wawEiJc9Co8g3WO2EwhKV6UrOiazJRard4+eZRWvegE=;
 c=relaxed/relaxed; d=dharmakit.com;
 h=to:cc:from:reply-to:subject:date:mime-version:content-type:list-id:list-unsubscribe:x-csa-complaints:list-unsubscribe-post:message-id:sender:x-sib-id:x-mailin-client:x-mailin-campaign:feedback-id:bimi-selector;
 q=dns/txt; s=brevo2; t=1758307098; v=1;
 b=qCvIdkY01A9JRJkMagzxh3guJfKouIGlAwRXyGH5pDYRYnjeUAifAe+7fYvcv6WRN2aZPCVy
 BuGCUsp4QO1xxMNlvhqrP9I8yR7Gy+N9q87xT+7pNpHRI05tlyAXQDOIS5AVT9zvzW8OODmNj3/
 hGBulURt5c5d8KLufkyEb/q8WVb2XxUZN+QbmPUPfpwLPFMwiTf5IapE0w6PNRazk5DEZckdnmH
 gOATNvT2W1KGV40p2uksPYfmrLYvkwu4WgvbrbTGCLCQ6iPA5w/KgvwRpdfCSJXgV1Z4291990s
 ERUDTVzcWadMXocl10WpodxC7pELVm1TaGrFlKxJ83z2Q==
DKIM-Signature: a=rsa-sha256; bh=wawEiJc9Co8g3WO2EwhKV6UrOiazJRard4+eZRWvegE=;
 c=relaxed/relaxed; d=mailin.fr;
 h=to:cc:from:reply-to:subject:date:mime-version:content-type:list-id:list-unsubscribe:x-csa-complaints:list-unsubscribe-post:message-id:sender:x-sib-id:x-mailin-client:x-mailin-campaign:feedback-id:bimi-selector;
 q=dns/txt; s=mail; t=1758307098; v=1;
 b=iwbSZ06Blcs+M0q5Dk65Uxb6NkGzwldkXdTHbo5xdI/pgX+wPUjEAYcFnYXXAPxGFI2wS6sH
 h23wT7aVt2inOQ1nhR1VyzUi5Xf/0b0X/25QuZJ+6nMIBiVtlSc0lUlwK+/MRiQj229ljjH8Bqw
 eoaLozoZKpxyqaNBYUW9TAhg=
To: <msniranjan2004@gmail.com>
Subject: =?utf-8?q?You=E2=80=99re_Shortlisted_=E2=80=93_Cyber_Security_Internship_?= =?utf-8?q?First_Selection_Round_=F0=9F=9A=80?=
Content-Type: multipart/alternative; boundary="-------?=_66130-3995251976281"
Date: Fri, 19 Sep 2025 18:38:18 +0000
Feedback-ID: 77.32.148.109:9885165_19:9885165:Sendinblue
From: HR Team <hr@dharmakit.com>
List-Id: OTg4NTE2NS0xODgzLTEz <OTg4NTE2NS0xODgzLTEz.list-id.mailin.fr>
List-Unsubscribe: <mailto:unsubscribe@ke.d.sender-sib.com?subject=unsub-2k20ihmhncnj&body=2k20ihmhncnj>,<https://haeu5.r.ag.d.sendibm3.com/mk/un/li/sh/SMJz09a0vkbXqUOY1aWF0gJuVAUb/uEGrjwm_U8Dr>
List-Unsubscribe-Post: List-Unsubscribe=One-Click
MIME-Version: 1.0
Message-Id: <202519091838.2k20ihmhncnj@ke.d.sender-sib.com>
Reply-To: <hr@dharmakit.com>
X-Csa-Complaints: csa-complaints@eco.de
X-Mailer: Sendinblue
X-Mailin-Campaign: 19
X-Mailin-Client: 9885165
X-sib-id: aBNnlL9lR6Id_Z1JdBYcoGWeSHlqXL258Rp1l2wRepOOn4h9VscWDP4v_CL_Une65R7J0b8FjMnnJsMHVRGi-cTYsuoe0QbDEh3HTvKjiXAWDZKofn-u7X3lI1JPWdR13XacuA_71nNmcRBZezWx46tGk8VRhzgDpSJLV4mRAHcWLVZu9dREic2pSX19gt8iEkHYN-YTUNIm0itkJdh9Hc-rQbUg9wg2zsA
```

## Evidence files to include in repo
- `raw_headers.txt` (paste full raw headers from the .eml).  
- `email_body.html` (the HTML part copied from the .eml).  
- screenshots: `auth_results.png`, `hover_link.png` (showing expanded link), `whois_dharmakit.png` (if you perform whois) — place in `/evidence`.
