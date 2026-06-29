# Frameworks de risco & segurança de IA — referência

> Condensado da pesquisa do repo MIT (`modulos/04-.../pesquisa/frameworks-risco-seguranca-ia.md`),
> pesquisada + verificada contra fontes oficiais em **27/jun/2026**. Reconferir versões antes de citar
> em material público — vários tiveram releases em 2025–2026.

## TL;DR — o stack (não competem, se empilham)
- **Moldura de processo:** **NIST CSF** — Identificar/Proteger/Detectar/Responder/Recuperar. Onde tudo
  se encaixa (é o do exercício do MIT).
- **Governança/risco de IA:** **NIST AI RMF** (grátis, backbone) · **ISO/IEC 42001** (quando precisa de
  selo auditável).
- **Ameaças/controles técnicos:** **OWASP Top 10 LLM/Agentic** · **MITRE ATLAS** · **Google SAIF**.
- **Lente legal:** **EU AI Act** (se toca a UE).

**Default p/ projetos do Bera (T1):** NIST CSF + NIST AI RMF (GenAI Profile, seletivo) + OWASP Top 10.
EU AI Act como checklist de transparência. ISO/SAIF/ATLAS = opt-in quando crescer.

## Tabela
| Framework | Tipo | Versão (ano) | Foco agêntico | Certificável | Esforço | Melhor para |
|---|---|---|---|---|---|---|
| NIST AI RMF | Gestão de risco | 1.0 (2023) + GenAI Profile (2024) | Baixo–médio | Não | Médio | Backbone de governança de risco; linguagem comum |
| OWASP Top 10 LLM/Agentic | Taxonomia de ameaças | LLM 2025 · Agentic 2026 | **Alto** | Não | Baixo | Ameaças técnicas concretas; threat modeling; hardening |
| MITRE ATLAS | Ameaças adversariais | dados v5.6.0 / release 2026.05 | Alto | Não | Médio | Red-team/SOC; TTPs adversariais de IA |
| ISO/IEC 42001 (+23894) | Mgmt system | 2023 (vigente 2026) | Baixo–médio | **Sim** | Alto | Selo auditável; governança enterprise; prova p/ EU AI Act |
| Google SAIF (+CoSAI) | Controles técnicos | SAIF 2.0 (2025) | **Alto** | Não | Baixo–médio | Secure-by-default; agentes; supply chain de ML |
| EU AI Act | Regulação | Reg. (UE) 2024/1689 (2024) | Baixo–médio | Obrigação legal | Alto | Compliance UE; classificação de risco; transparência |

## Perfis curtos

**NIST AI RMF (+ GenAI Profile).** Framework voluntário do NIST; funções GOVERN/MAP/MEASURE/MANAGE
(rimam com o CSF). GenAI Profile traz 12 riscos concretos de IA generativa com ações. *Use como:*
backbone de governança; em projeto pequeno, modo seletivo (subconjunto de subcategorias). *Não dá:*
selo, controles técnicos passo-a-passo, módulo agêntico explícito.
Fontes: nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf · /NIST.AI.600-1.pdf · nist.gov/itl/ai-risk-management-framework

**OWASP Top 10 LLM/Agentic.** Catálogo comunitário de ameaças de apps de LLM (LLM01–10, 2025) e de
agentes (ASI01–10, 2026), com mitigações acionáveis. *Use como:* checklist técnico do que pode dar
errado + como impedir. *Atenção:* nomenclatura ASI ainda oscila (ex.: "Agent Behavior Hijacking" vs
"Agent Goal Hijack") — conferir no PDF oficial. Fontes: genai.owasp.org/llm-top-10/ ·
genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/

**MITRE ATLAS.** Base viva (estilo ATT&CK) de táticas/técnicas adversariais contra IA: 16 táticas, ~170
técnicas, 35+ mitigações, 57+ casos reais. Release "Secure AI v2" (mai/2026), cadência mensal. *Use
como:* biblioteca de ameaças p/ threat modeling e red-team. *Não dá:* processo de governança. Fontes:
atlas.mitre.org · github.com/mitre-atlas/atlas-data

**ISO/IEC 42001 (+23894).** 42001:2023 = sistema de gestão de IA **certificável** (estilo 27001), Anexo
A com 38 controles; 23894:2023 = guidance de risco (espelha ISO 31000). Ecossistema cresceu (42005:2025
impact assessment, 42006:2025 requisitos de certificadores). *Use como:* selo auditável p/ cliente/
regulador. *Não dá:* controles técnicos; é norma paga. Fontes: iso.org/standard/42001 · /77304.html

**Google SAIF (+CoSAI).** SAIF 2.0 (2025) = secure-by-default ao longo de Data/Infra/Model/App, com foco
em "Secure Agents"; CoSAI (OASIS) transforma em padrões abertos (model signing, IR framework, MCP).
*Use como:* camada de controles técnicos secure-by-default + agentes. *Atenção:* origem vendor (Google).
Fontes: saif.google/secure-ai-framework · oasis-open.org (CoSAI)

**EU AI Act (Reg. (UE) 2024/1689).** Regulação vinculativa, baseada em risco (inaceitável/alto/limitado/
mínimo) + regras GPAI. Em vigor desde 1/ago/2024; "Digital Omnibus" (votado no Parlamento em 16/jun/2026)
adia obrigações do Anexo III p/ 2/dez/2027 e Anexo I p/ 2/ago/2028. *Use como:* lente legal — classificar
risco, rotular saída de IA (Art. 50), evitar práticas proibidas (Art. 5). Para projeto pequeno: quase
sempre risco mínimo/transparência. Fontes: digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai ·
eur-lex.europa.eu (OJ:L_202401689)

## Mapeamento às 5 funções do NIST CSF (resumo)
- **Identificar:** NIST AI RMF (MAP), ISO 42001 (contexto/6.1.2), EU AI Act (classificação de risco),
  OWASP/ATLAS (catálogo de ameaças = inventário de superfície).
- **Proteger:** OWASP (validação de output, least-privilege em tools), SAIF (secure-by-default, model
  signing), ISO 42001 (Anexo A), EU AI Act (Arts. 14/15).
- **Detectar:** ATLAS (técnicas → detecção/telemetria), OWASP (indicadores), EU AI Act (logging Art. 12).
- **Responder:** SAIF/CoSAI (AI Incident Response Framework), OWASP (contenção), EU AI Act (reporte Art. 73).
- **Recuperar:** ponto fraco de quase todos → CSF + ISO 22301/27001 lideram.
