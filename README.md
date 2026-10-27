# HTTP Proxy Router & Defense Console

> Servidor proxy reverso com roteamento condicional de tráfego, classificação de ameaças e telemetria em tempo real — em produção em VPS Oracle Cloud.

🔗 **Live Demo:** [phrobots.com.br](https://phrobots.com.br)

---

## 📌 Visão Geral

O **HTTP Proxy Router** é um servidor de segurança de rede desenvolvido do zero em Python, atuando como um **Firewall de Aplicação / Reverse Proxy HTTP** com capacidade de:

- **Inspecionar** payloads e headers de requisições em tempo real
- **Classificar** tráfego entre legítimo, bots, crawlers e ameaças
- **Rotear condicionalmente** com base na análise (CLEAN → QUARANTINE → SANITIZED)
- **Monitorar** via dashboard 3D com gráficos de telemetria ao vivo

---

## ⚙️ Arquitetura

```
Internet → Nginx (SSL) → FastAPI Router → Threat Classifier
                                        ├── CLEAN_ROUTE    → Produção (200 OK)
                                        ├── QUARANTINE     → Honeypot (403/307)
                                        └── SANITIZED      → Filtro + liberação
```

---

## 🧠 Módulos

| Módulo | Descrição |
|---|---|
| `threat_classifier.py` | Classificação de tráfego com análise Laplaciana e FFT |
| `auth_db.py` | Autenticação JWT com controle de acesso e audit trail |
| `http_router.py` | Roteamento condicional HTTP |
| `jwt_handler.py` | Geração e validação de tokens JWT |
| `link_manager.py` | Gerenciamento de rotas e redirecionamento |
| `tunnel_manager.py` | Gestão de túneis e conexões persistentes |
| `privacy_engine.py` | Sanitização e proteção de dados sensíveis |
| `retention_manager.py` | Política de retenção de logs |

---

## 🚀 Stack Tecnológica

![Python](https://img.shields.io/badge/Python-3.11-blue?style=flat-square&logo=python)
![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-green?style=flat-square&logo=fastapi)
![Nginx](https://img.shields.io/badge/Nginx-Reverse_Proxy-009639?style=flat-square&logo=nginx)
![Oracle Cloud](https://img.shields.io/badge/Oracle_Cloud-VPS-F80000?style=flat-square&logo=oracle)
![Three.js](https://img.shields.io/badge/Three.js-3D_Dashboard-black?style=flat-square&logo=threedotjs)

- **Back-end:** Python 3.11, FastAPI, SQLite
- **Segurança:** JWT, SSL/HTTPS, rate limiting, honeypot routing
- **Infra:** Oracle Cloud VPS, Ubuntu Server, Nginx, systemd service
- **Front-end:** HTML/CSS/JS, Three.js (globo 3D), Chart.js (telemetria ao vivo)

---

## 📊 Dashboard ao Vivo

Acesse: **[phrobots.com.br](https://phrobots.com.br)**

- 🌐 Globo 3D interativo com conexões de rede
- 📈 Gráficos de latência e throughput em tempo real
- 🔍 Audit trail com classificação de requisições
- 🚨 Alertas de ameaças detectadas

---

## 🛠️ Como Executar

```bash
git clone https://github.com/paulobankai/http-proxy-router.git
cd http-proxy-router
pip install -r requirements.txt
python main.py
```

---

## 📁 Estrutura

```
http-proxy-router/
├── main.py
├── requirements.txt
├── core/
│   ├── threat_classifier.py
│   ├── auth_db.py
│   ├── http_router.py
│   ├── jwt_handler.py
│   ├── link_manager.py
│   ├── tunnel_manager.py
│   ├── privacy_engine.py
│   └── retention_manager.py
├── server/
├── deploy/
└── gui/
```

---

## 👤 Autor

**Paulo Henrique Matos de Souza**
🔗 [phrobots.com.br](https://phrobots.com.br) · 📧 paulohenriquems1975@gmail.com

> *Desenvolvido com AI-Assisted Development: engenharia de prompts, depuração analítica e refatoração assistida por IA.*
