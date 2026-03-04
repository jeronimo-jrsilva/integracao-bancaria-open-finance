# 🛡️ Especificação de Segurança: mTLS e OAuth2

Este documento detalha os protocolos de segurança adotados no projeto **Integração Bancária Open Finance**, justificando sua escolha com base nas normas do **Banco Central do Brasil (BCB)**.

## 1. mTLS (Mutual Transport Layer Security)
O mTLS é a base da confiança no ecossistema do Open Finance Brasil. Diferente do TLS padrão, onde apenas o servidor é autenticado, o mTLS exige que **ambas as partes** apresentem certificados digitais válidos.

### 🔹 Por que mTLS?
- **Identidade Bilateral:** O banco garante que está falando com o *Software Alpha*, e o software garante que está falando com o endpoint real do banco.
- **Certificados ICP-Brasil:** O uso de certificados de nível militar (e-PJ ou específicos de Open Banking) impede o acesso de atores não autorizados, mesmo que possuam credenciais de API.
- **Integridade do Canal:** Garante que os dados trafeguem em um túnel criptografado, protegendo informações sensíveis de extratos e saldos contra interceptação (*Man-in-the-Middle*).

## 2. OAuth2 (Autorização Segura)
Enquanto o mTLS protege a "estrada", o OAuth2 gerencia o "acesso às salas". É o protocolo que permite ao usuário final autorizar o sistema a ler seus dados sem nunca compartilhar sua senha bancária.

### 🔹 Por que OAuth2?
- **Consentimento Granular:** O usuário autoriza apenas o que é necessário (ex: leitura de extratos), por um período determinado.
- **Tokens Temporários (JWT):** O sistema utiliza *Access Tokens* de curta duração. Caso um token seja comprometido, ele expira rapidamente, minimizando riscos.
- **Segurança Delegada:** O processo de autenticação ocorre no ambiente seguro do banco. O *Software Alpha* recebe apenas uma permissão assinada, nunca a senha do cliente.

## 3. Sinergia dos Protocolos
No fluxo do Open Finance, esses protocolos trabalham em camadas:
1. **Camada de Conexão (mTLS):** Estabelece o canal seguro entre o servidor do Software e o Servidor do Banco.
2. **Camada de Aplicação (OAuth2):** Valida se o usuário dono da conta autorizou aquela operação específica.

---
*Documento gerado para fins acadêmicos na disciplina de Análise de Conformidade.*
