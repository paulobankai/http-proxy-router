# HTTP Proxy Router & Defense Console

> Servidor proxy reverso com roteamento condicional de tráfego, classificação de ameaças e telemetria em tempo real — em produção em VPS Oracle Cloud.

🔗 **Live Demo:** [phrobots.com.br](https://phrobots.com.br)

--- 

## 📸 Screenshots

> Dashboard ao vivo em [phrobots.com.br](https://phrobots.com.br)

### Painel Administrativo
![Painel Administrativo](Painel%20adm.png)

### Configuração de Links
![Configuração de Links](Configuração%20de%20links.png)

### Configurações de Link 2
![Configurações de Link 2](Configurações%20de%20link%202.png)

### Monitoramento de Acesso aos Links
![Monitoramento de Acesso aos Links](Monitoramento%20de%20acesso%20aos%20links.png)

### Monitoramento de Bloqueio
![Monitoramento de Bloqueio](Monitoramento%20de%20bloqueio.png)

### Monitoramento de IP
![Monitoramento de IP](Monitoramento%20de%20ip.png)

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
