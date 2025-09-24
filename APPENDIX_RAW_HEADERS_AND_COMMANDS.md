# Appendix — Raw Headers & Reproducible Command List

## Raw headers (full dump)
The full raw headers from the uploaded `.eml` are below (copied verbatim). Use these for header analysis and to reproduce the checks.

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

---

## Reproducible command list (run from Linux / WSL / macOS terminal)

> **Note:** Replace `<domain>` or `<url>` placeholders with the actual domain or URL you want to inspect. Be careful — do not execute or open any suspicious links in your main environment.

### 1) View Received chain and resolve IPs
# show DNS A records
dig +short <domain>

# resolve host to IP
nslookup <domain>

# show full dig output (useful to see authoritative nameservers)
dig <domain> ANY +noall +answer

### 2) WHOIS lookup (domain registration info)
whois <domain>

# If whois is not installed:
# On Debian/Ubuntu:
sudo apt update && sudo apt install -y whois

### 3) Check SSL certificate (see issuer and CN)
# Use openssl to connect and show certificate chain
echo | openssl s_client -connect <domain>:443 -servername <domain> 2>/dev/null | openssl x509 -noout -text

### 4) Expand redirects for a given URL (do NOT open in browser)
# Get response headers to see Location redirects (follows only with -L)
curl -I -L -s -S "<url>"

# Show initial response (no follow), to inspect intermediate Location header:
curl -I -s -S "<url>"

# To safely follow redirects and print each step:
curl -s -S -I -L -o /dev/null -w "%{{url_effective}}\n" -D - "<url>"

### 5) Check IP reputation / geolocation
# Lookup ASN and who owns IP
whois <ip_address>

# Quick geolocation (requires 'geoiplookup' package):
geoiplookup <ip_address>

### 6) VirusTotal (manual)
# VirusTotal does not allow anonymous CLI heavy use; use web UI:
# - Upload the suspicious attachment or paste the suspicious URL at https://www.virustotal.com
# - Save screenshots of the results (e.g. 12/70 engines detection)

### 7) Header analysis (online & local)
# Option A (online): Paste raw headers into an Email Header Analyzer (search "email header analyzer") and review the parsed Received chain and SPF/DKIM results.
# Option B (local): Examine headers manually (look for Authentication-Results, Return-Path, Received entries).

### 8) Example commands using the actual Sendinblue IP seen in this message (replace IP with observed one)
# Reverse DNS
dig -x 77.32.148.109 +short

# WHOIS for IP
whois 77.32.148.109

---

## Tips for documenting findings
- Copy and paste relevant header lines (Authentication-Results, Received lines) verbatim into your report.
- Take screenshots of any online tools you use (Header analyzer, VirusTotal, WHOIS web UI) and save under `/evidence`.
- When inspecting links: prefer to expand the redirect and confirm final landing host — if it matches the employer domain and HTTPS certificate CN, it's more reassuring.
