# API de Cotações Inteligentes

Uma API para consulta inteligente de preços de produtos, com **MySQL para persistência** e **Redis para otimização**.  
O projeto foi criado para demonstrar **boas práticas de arquitetura backend**, **regras de negócio personalizadas** e **uso eficiente de cache**.

---

## Funcionalidades
- Consulta de preço médio de produtos baseada no histórico.
- Limite de cotações por usuário (anti-abuso).
- Cache inteligente para respostas rápidas.
- Histórico detalhado de preços por produto.
- Estatísticas de uso da API.

---

## Tecnologias Utilizadas
- **Linguagem:** [Java + Spring Boot]
- **Banco de dados:** MySQL
- **Cache:** Redis
- **Documentação:** Swagger/OpenAPI

---

## Regras de Negócio
1. **Limite de 10 cotações/hora por usuário** → controlado pelo Redis.
2. **Cache de 6 horas para preços** → evita consultas desnecessárias ao banco.
3. **Cálculo de preço médio** com base no histórico do Banco de dados.
4. **Invalidação automática de cache** quando houver variação significativa no preço.

---

## Exemplos de Uso
### Solicitar uma cotação
POST /quotation
```json
{
  "product_id": 12
}
```
### Resposta

```json
{
  "product_id": 12,
  "product_name": "Placa de Vídeo RTX 4070",
  "average_price": 3450.75,
  "cached": true
}
```
