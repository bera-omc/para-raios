# para-raios — spec & design

## Propósito
Skill reutilizável que gera um **plano de risco & segurança de IA** para qualquer projeto do Bera,
escalado ao tamanho (solo → enterprise). Transforma o aprendizado da Atividade 4 do MIT (checklist
NIST CSF) + a pesquisa comparativa de frameworks de IA em uma ferramenta acionável e reaproveitável.

## Origem
- **Atividade 4** do Módulo 4 (Cibersegurança e riscos de agentes), MIT IA Agêntica.
- **Pesquisa multi-agente + verificação** de 6 frameworks (27/jun/2026), documentada em
  `modulos/04-ciberseguranca-riscos-agentes/pesquisa/frameworks-risco-seguranca-ia.md` (repo MIT).

## Decisões de design
- **Trigger: manual-only / nominal.** Segue a regra global do Bera (não auto-invocar skills). Mesmo
  padrão de `huashu-design` e `tags-bera`.
- **Backbone: NIST CSF + NIST AI RMF.** Gratuitos, flexíveis, mapeiam direto no exercício do curso e
  são reconhecidos por C-level. As 5 funções são a moldura onde tudo se pendura.
- **Conteúdo técnico: OWASP + MITRE ATLAS + SAIF.** Biblioteca de ameaças/controles (o "o que pode dar
  errado e como evitar") — a camada que a governança abstrata não dá.
- **Lente legal: EU AI Act (lite).** Checklist de transparência + práticas proibidas; completo só em T3.
- **ISO/IEC 42001: opt-in (T3).** Só quando há necessidade de selo auditável.
- **Escala por tier (T1/T2/T3).** Evita over/under-engineering — o erro mais comum num plano de risco.

## Por que "para-raios"
Aterra o risco antes de virar incidente. Persona memorável p/ palestra; alinha com o estilo de
skills-persona do Bera (pasteleiro, bola-de-cristal).

## Não-objetivos
- Não é auditoria de segurança automatizada (não roda scanners/pentest).
- Não substitui consultoria jurídica de compliance (EU AI Act aqui é orientação, não parecer).
- Não implementa correções — produz o **plano**; a execução é decisão à parte.

## Manutenção
Frameworks mudam rápido. Revisar `references/frameworks.md` periodicamente (tem data da pesquisa).
Candidatos a próxima atualização: NIST AI RMF 2.0 (em revisão em 2026), nomenclatura OWASP Agentic
(ASI01–ASI10 ainda estabilizando), releases mensais do MITRE ATLAS.

## Como evoluir esta skill
Use o `skill-creator` (`/skill-creator`) para rodar evals de trigger e otimizar a `description` se o
disparo ficar impreciso. Para adicionar um framework, crie/atualize a seção em
`references/frameworks.md` e, se ele trouxer ameaças novas, em `references/threat-library.md`.
