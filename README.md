# AWS Step Functions: Estudo e Projeto Prático

Este repositório documenta minha experiência prática com o **AWS Step Functions**, abordando desde o conhecimento teórico até a execução de um projeto modelo, com validações e integrações usando AWS Lambda.

---

## 🔍 Tópicos Abordados

### 1. Conhecendo o AWS Step Functions
O AWS Step Functions é um orquestrador de workflows serverless que facilita a coordenação de múltiplos serviços AWS em fluxos de trabalho visuais. Com ele, podemos definir lógicas de execução, paralelismo, tentativas automáticas e muito mais.

👉 [Saiba mais sobre o AWS Step Functions](https://aws.amazon.com/pt/step-functions/)

**Principais conceitos:**
- **State Machine (Máquina de Estados)**: Define a lógica do fluxo.
- **States**: Passos no fluxo (Task, Choice, Pass, Fail, Succeed).
- **Transitions**: Definem a sequência entre os estados.

### 2. Benefícios do AWS Step Functions
- Orquestração visual de processos.
- Integração nativa com serviços AWS (Lambda, DynamoDB, SQS, etc).
- Gerenciamento automático de erros.
- Escalabilidade e alta disponibilidade.
- Monitoramento detalhado via CloudWatch.

### 3. Projeto Modelo no AWS Step Functions

Criei um projeto simples que simula o seguinte fluxo:
- **Receber dados de entrada**
- **Executar uma função Lambda**
- **Validar os dados retornados**
- **Encerrar com sucesso ou erro**

🔧 O arquivo `state-machine-definition.json` contém a definição da máquina de estados.

### 4. Validações no Step Functions

Utilizei o recurso de **Choice State** para validar:
- Se um número retornado pela Lambda é par ou ímpar.
- Em caso de erro, redirecionar o fluxo para um estado de falha.
  
Exemplo:
```json
{
  "Type": "Choice",
  "Choices": [
    {
      "Variable": "$.resultado",
      "NumericEquals": 0,
      "Next": "NumeroPar"
    }
  ],
  "Default": "NumeroImpar"
}

