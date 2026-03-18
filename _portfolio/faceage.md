---
title: "FaceAge Web Application"
excerpt: "Full-stack clinical research platform for IRB-approved FaceAge studies at Mass General Brigham"
collection: portfolio
---

**Clinical Research Platform | MGB**
**Production:** [faceage.bwh.harvard.edu](https://faceage.bwh.harvard.edu)

---

Designed and built a full-stack clinical research web application enabling IRB-approved studies to collect facial photographs from participants and estimate biological age using the FAHR-Face deep learning model. The system is deployed in production at MGB under two IRB protocols (healthy volunteer and MGB patient arms).

**Key responsibilities and technical contributions:**

- **Full-stack development** using Python/Flask (Gunicorn, 5 gevent workers), with Jinja2 templating, Bootstrap front-end, and SQLAlchemy/SQLite for authentication data
- **Deep learning inference pipeline**: deployed FAHR-Face — a 12-layer Vision Transformer (ViT) with a linear regression head on the [CLS] token, operating on 112×112 aligned face crops; weights loaded at runtime from a volume-mounted checkpoint; RetinaFace used for face detection and alignment; per-session median age computed across multiple images and age delta calculated against chronological DOB; results returned to participants asynchronously by email
- **Asynchronous task architecture**: designed a Redis Queue (RQ) system with a scheduler container polling REDCap every 60 seconds, enqueuing face-age jobs picked up by a dedicated worker container
- **Third-party integrations**: REDCap API (participant records, questionnaire data, results), Dropbox API (photo storage and file request links), MGB internal SMTP relay (automated transactional emails)
- **Authentication and security**: implemented full participant auth flow (bcrypt, token-based account activation, password reset, session management, account lockout); added CSRF protection (Flask-WTF), security headers (Flask-Talisman/HSTS), and Redis distributed locking to prevent race conditions on concurrent registrations
- **Containerised deployment**: orchestrated 5-container Docker Compose stack (nginx reverse proxy with SSL termination, Flask app, RQ worker, RQ scheduler, Redis); cross-platform multi-arch builds (`docker buildx`) for Apple Silicon → amd64 Linux server
- **E-consent and data capture**: built a multi-step participant flow covering study-arm selection, electronic consent with PDF generation, baseline and daily questionnaires, and photo upload (file or webcam)

**Tech stack:** Python · Flask · Gunicorn · SQLAlchemy · Redis · RQ · Docker · nginx · PyTorch · HuggingFace Transformers (ViT) · RetinaFace · REDCap API · Dropbox API · SQLite · Flask-WTF · Flask-Talisman · Flask-Mail

---

**Underlying model:** Haugg F, Lee G, He J, Nürnberg L, Bontempi D, Bitterman DS, Catalano P, Prudente V, Glubokov D, **Warrington A**, et al. *Foundation Artificial Intelligence Models for Health Recognition Using Face Photographs (FAHR-Face)*. arXiv:2506.14909. Under review at *Lancet Digital Health*. [arXiv](https://arxiv.org/abs/2506.14909)
