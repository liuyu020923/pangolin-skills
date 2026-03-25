# pangolinfo-ai-serp — Terminal 教程

> Google SERP + AI Overview 搜索技能 | AI Mode 2 积分/次 | SERP 0.5 积分/次

---

### 1. 挂载安装与 API 认证

```bash
user@openclaw:~$ export PANGOLIN_API_KEY="pgl_a1b2c3d4exxx"

user@openclaw:~$ python3 -m clawhub install pangolinfo-ai-serp

  ✓ Skill installed → ~/.openclaw/skills/pangolinfo-ai-serp
```

### 2. AI Mode 搜索（Google AI Overview）

```bash
user@openclaw:~$ python3 scripts/pangolin.py --q "what is quantum computing"

  > [Pangolin API] AI Mode search: "what is quantum computing"...
  > [Parser: googleAISearch] Extracting AI overview + references...

  {
    "success": true,
    "ai_overview": [{
      "content": [
        "Quantum computing uses quantum bits (qubits) that can exist in",
        "multiple states simultaneously through superposition. Unlike",
        "classical bits (0 or 1), qubits enable parallel computation,",
        "making quantum computers exponentially faster for specific tasks",
        "like cryptography, drug discovery, and optimization problems."
      ],
      "references": [
        {"title": "Quantum Computing - IBM", "url": "https://www.ibm.com/quantum"},
        {"title": "Quantum Computing - Wikipedia", "url": "https://en.wikipedia.org/wiki/Quantum_computing"}
      ]
    }]
  }
```

### 3. 标准 SERP 搜索（传统 Google 结果 + 截图）

```bash
user@openclaw:~$ python3 scripts/pangolin.py --q "best databases 2025" \
                    --mode serp --region us --screenshot

  > [Pangolin API] SERP search: "best databases 2025" (region: us)...
  > [Parser: googleSearch] Extracting organic results...
  > [Screenshot] Capturing Google results page...

  {
    "success": true,
    "results_num": 10,
    "organic_results": [
      {"title": "Top 10 Databases for 2025", "url": "https://db-engines.com/...",
       "text": "PostgreSQL leads the ranking for the third year running..."},
      {"title": "Best Databases Compared", "url": "https://www.g2.com/...",
       "text": "MongoDB, Redis, and DynamoDB round out the top 5..."},
      ...
    ],
    "screenshot": "https://image.pangolinfo.com/screenshots/serp_2025xxxx.png"
  }
```

### 4. 多轮追问对话（AI Mode 连续提问）

```bash
user@openclaw:~$ python3 scripts/pangolin.py --q "kubernetes" \
                    --follow-up "how to deploy to production" \
                    --follow-up "monitoring best practices"

  > [Pangolin API] AI Mode: "kubernetes" + 2 follow-ups...
  > [Turn 1/3] Initial query...
  > [Turn 2/3] Follow-up: "how to deploy to production"...
  > [Turn 3/3] Follow-up: "monitoring best practices"...

  {
    "success": true,
    "ai_overview": [{
      "content": [
        "For production Kubernetes deployment, use managed services like",
        "EKS, GKE, or AKS. Key practices: use namespaces for isolation,",
        "set resource limits, enable RBAC, and use Helm for packaging.",
        "",
        "For monitoring, the standard stack is Prometheus + Grafana for",
        "metrics, with Loki or ELK for log aggregation. Consider also",
        "Datadog or New Relic for full-stack observability."
      ],
      "references": [
        {"title": "Kubernetes Production Best Practices", "url": "https://learnk8s.io/production-best-practices"},
        {"title": "Monitoring Kubernetes", "url": "https://prometheus.io/docs/"}
      ]
    }]
  }
```

---

> AI Mode 2 积分/次 | SERP 0.5 积分/次 | 追问建议 ≤5 轮 | 详见 SKILL.md 获取完整 CLI 参数列表
