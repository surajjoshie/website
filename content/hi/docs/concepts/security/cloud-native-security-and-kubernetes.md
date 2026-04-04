# Cloud Native Security and Kubernetes

क्लाउड नेटिव वर्कलोड को सुरक्षित (secure) रखने के लिए महत्वपूर्ण अवधारणाएँ।

Kubernetes एक **cloud native architecture** पर आधारित है और यह CNCF द्वारा बताए गए cloud native information security के best practices का पालन करता है।

इस दस्तावेज़ में आप समझेंगे कि Kubernetes कैसे एक सुरक्षित cloud native platform बनाने और चलाने में मदद करता है।

---

## Cloud native information security

CNCF white paper के अनुसार cloud native security में अलग-अलग **lifecycle phases** के लिए security controls और best practices पर ध्यान दिया जाता है।

---

## Develop lifecycle phase (विकास चरण)

इस चरण में focus होता है development environment की सुरक्षा और integrity पर।

- development environments की integrity को सुनिश्चित करें।
- applications को information security के सिद्धांतों के अनुसार design करें।
- end user security को हमेशा design का हिस्सा बनाएं।

इसे प्राप्त करने के लिए:

- **zero trust architecture** अपनाएं, जिससे attack surface कम हो जाता है।
- ऐसा code review process लागू करें जिसमें security को प्राथमिकता दी जाए।
- system का **threat model** बनाएं और trust boundaries को identify करें।
- risks को समझकर उनके लिए proper mitigation करें।
- advanced security practices जैसे **fuzzing** और **security chaos engineering** का उपयोग करें जहाँ आवश्यक हो।

---

## Distribute lifecycle phase (वितरण चरण)

इस चरण में software supply chain की सुरक्षा सबसे महत्वपूर्ण होती है।

- container images की security सुनिश्चित करें।
- cluster और उसके components की security सुनिश्चित करें (जैसे external database, storage systems)।

इसे प्राप्त करने के लिए:

- container images और artifacts को vulnerabilities के लिए scan करें।
- software distribution को encrypted in transit रखें।
- trusted source chain और verification का उपयोग करें।
- dependencies को समय पर update करें, खासकर security patches के बाद।
- digital certificates जैसे validation mechanisms अपनाएं।
- security feeds और alerts को subscribe करें।
- container images को **private registry** में रखें और access control लागू करें।

---

## Deploy lifecycle phase (तैनाती चरण)

इस चरण में control होता है कि क्या deploy होगा, कौन करेगा और कहाँ होगा।

- deployments को strictly control करें।
- cryptographic verification को enforce करें।
- workloads को अलग-अलग **namespaces** में deploy करें।

Kubernetes infrastructure यहाँ एक secure foundation बनाता है जिस पर applications चलते हैं।

---

## Runtime lifecycle phase (रनटाइम चरण)

Runtime phase में तीन मुख्य हिस्से होते हैं: **access, compute, storage**।

---

### Runtime protection: access (एक्सेस सुरक्षा)

- Kubernetes API पूरे cluster का core होता है, इसकी security सबसे महत्वपूर्ण है।
- proper authentication और authorization configure करें।
- **ServiceAccounts** का उपयोग करके workloads की identity manage करें।
- Kubernetes API traffic को secure करने के लिए **TLS** का उपयोग करें।
- encryption keys को सुरक्षित रखें और misuse से बचाएं।

---

### Runtime protection: compute (कम्प्यूट सुरक्षा)

Containers isolation और resource sharing दोनों प्रदान करते हैं, इसलिए balance जरूरी है।

सुरक्षा के लिए:

- **Pod Security Standards** लागू करें।
- container-optimized immutable OS का उपयोग करें।
- **ResourceQuotas** और **LimitRanges** सेट करें।
- workloads को अलग-अलग nodes पर isolate करें।
- secure container runtime का उपयोग करें।
- Linux security modules जैसे **AppArmor** और **seccomp** enable करें।

---

### Runtime protection: storage (स्टोरेज सुरक्षा)

- external storage systems में encryption at rest enable करें।
- Kubernetes API objects को encrypt करें।
- नियमित backups लें और restore test करें।
- storage और nodes के बीच secure authentication रखें।
- application-level encryption लागू करें।
- encryption keys के लिए **Hardware Security Module (HSM)** का उपयोग करें।

---

## Networking and security (नेटवर्क सुरक्षा)

- **NetworkPolicy** और **service mesh** का उपयोग करें।
- network plugins data-in-transit encryption दे सकते हैं।
- सही networking plugin चुनना security पर बड़ा प्रभाव डालता है।

---

## Observability and runtime security (मॉनिटरिंग और सुरक्षा)

- logs, metrics और monitoring systems को secure रखें।
- third-party observability tools का सही उपयोग करें।
- पूरे data pipeline की integrity सुनिश्चित करें।
- **cryptographically measured boot** जैसे low-level security controls लागू करें।
- logs को tamper-proof और secure रखना बहुत जरूरी है।

---

##आगे क्या है

- Cloud native security
- CNCF white paper on cloud native security
- Secure software supply chain practices
- Kubernetes Security Best Practices
- Data encryption in transit
- Data encryption at rest
- Secrets in Kubernetes
- Network policies for Pods
- Pod Security Standards
- RuntimeClasses
