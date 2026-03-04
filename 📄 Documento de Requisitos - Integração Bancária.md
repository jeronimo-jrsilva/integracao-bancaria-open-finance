---
tipo: projeto
titulo: "📄 Documento de Requisitos - Integração Bancária Open Finance"
disciplina: "Análise de Conformidade"
autor: "Daniela Ferreira, Fábio Mandu, Rafael Fiurza e Jeronimo Silva"
data: 2026-03-04
---

# 📄 Documento de Requisitos - Integração Bancária Open Finance

## 1. Introdução
Este documento descreve as necessidades funcionais e regras de negócio para o módulo de integração entre o **Software Contábil Alpha** e instituições financeiras via **Open Banking (APIs)**. O objetivo é automatizar a conciliação bancária, o monitoramento de pagamentos e o recálculo automático de encargos tributários em caso de inadimplência.

## 2. Requisitos Funcionais (RF)

- **RF01 - Integração Open Finance:** O sistema deve consumir APIs bancárias padronizadas para obter extratos e status de títulos em tempo real.
- **RF02 - Conciliação Automática:** O sistema deve cruzar automaticamente os registros de "Contas a Pagar" com os eventos de saída do extrato bancário.
- **RF03 - Varredura de Status (Sentinel):** O sistema deve executar uma rotina diária às 23:59 para verificar títulos com vencimento em D+0.
- **RF04 - Recálculo de Encargos:** O sistema deve calcular automaticamente multa, juros e atualização monetária sobre títulos em atraso.
- **RF05 - Log de Auditoria:** O sistema deve registrar detalhadamente cada alteração de status e recálculo de valores, incluindo data, hora e justificativa técnica.

## 3. Requisitos Não-Funcionais (RNF)

- **RNF01 - Segurança da Comunicação:** Toda troca de dados via API deve utilizar protocolos de criptografia TLS 1.3 e autenticação via mTLS/OAuth2.
- **RNF02 - Disponibilidade:** O serviço de varredura (Sentinel) deve ter disponibilidade de 99.9% para garantir o processamento no fechamento do dia.
- **RNF03 - Conformidade Legal:** Os cálculos de juros e multas devem seguir estritamente a legislação tributária brasileira vigente.

## 4. Regras de Negócio (RN)

- **RN01 - Mudança de Status:** Se um título com vencimento em D+0 não apresentar evento de saída correspondente até às 23:59, seu status deve ser alterado para **"Falta Pagamento"**.
- **RN02 - Aplicação de Multa:** Em caso de atraso, deve-se aplicar multa fixa de **2%** sobre o valor original do título.
- **RN03 - Juros de Mora:** Deve-se aplicar juros de **1% ao mês**, calculados *pro rata die* (por dia de atraso).
- **RN04 - Atualização Monetária:** Para atrasos superiores a 30 dias, o sistema deve aplicar o índice **IPCA** (ou IGPM conforme contrato) para correção do valor principal.

---
