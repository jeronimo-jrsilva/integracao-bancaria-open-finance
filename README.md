# Projeto Integração Bancária Open Finance 🚀

Este repositório contém a documentação técnica para o módulo de integração bancária automatizada, desenvolvido como parte da disciplina de **Análise de Conformidade** (Graduação em ADS - Senac).

## 📝 Visão Geral
O projeto visa solucionar o gargalo da conciliação bancária manual em softwares contábeis, utilizando as APIs do **Open Finance** para monitorar pagamentos em tempo real e automatizar o recálculo de encargos tributários.

Para entender mais sobre o ecossistema, veja: [O que é Open Finance?](./docs/OPEN_FINANCE.md).

## ✨ Principais Funcionalidades (Conceitual)
- **Integração Open Finance:** Consumo de APIs bancárias para extratos e status de títulos.
- **Conciliação Inteligente:** Cruzamento automático de "Contas a Pagar" com eventos de saída bancária.
- **Monitoramento Sentinel (23:59):** Varredura automática no final do dia para identificação de inadimplência em D+0.
- **Recálculo Automático de Encargos:** Aplicação imediata de multas (2%), juros (1% p.m.) e correção monetária (IPCA).
- **Trilha de Auditoria:** Log detalhado de todas as operações para conformidade técnica e legal.

## 🛡️ Conformidade e Segurança
- **Segurança:** Autenticação via mTLS e OAuth2 (Padrão Open Banking Brasil).
- **Legislação:** Cálculos baseados na legislação tributária brasileira vigente.
- **Protocolos:** Criptografia TLS 1.3 para tráfego de dados sensíveis.
- **Detalhes Técnicos:** Veja a [Especificação de Segurança](./docs/SEGURANCA.md).

## 🎓 Contexto Acadêmico
- **Disciplina:** Análise de Conformidade
- **Instituição:** Faculdade Senac
- **Autores:** Daniela Uchôa, Fabio Mandu, Rafel Fiurza, Jeronimo Silva
- **Status:** Em fase de especificação de requisitos.

---
*Este é um projeto com fins didáticos para demonstração de Engenharia de Requisitos e Conformidade de Software.*
