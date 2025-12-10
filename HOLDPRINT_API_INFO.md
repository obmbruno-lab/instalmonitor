# Informações da API Holdprint

## ✅ Configuração Atual (Funcionando)

### Endpoint Testado e Validado
```
GET https://api.holdworks.ai/api-key/jobs/data
```

### Header de Autenticação
```
x-api-key: <sua_chave_api>
```

### Chaves Configuradas
- **São Paulo (SP)**: `4e20f4c2-6f84-49e7-9ab9-e27d6930a13a`
- **Porto Alegre (POA)**: `84ae7df8-893c-4b0d-9b6e-516def1367f0`

### Formato de Resposta
```json
{
  "data": [
    {
      "id": "692cff0eb27f50c6ed40bc67",
      "code": 1146,
      "title": "Fórmula 1 - Las Vegas",
      "type": "ApprovedBudget",
      "customerName": "WASSERMAN - LIVE",
      ...
    }
  ]
}
```

## ❌ Endpoints Testados que NÃO Funcionam

| Endpoint | Header | Status |
|----------|--------|--------|
| `/api/v1/jobs` | `Api-Key` | 404 Not Found |
| `/api/v1/jobs` | `Authorization: Bearer` | 404 Not Found |
| `/api/v1/jobs` | `x-api-key` | 404 Not Found |
| `/api/v1/jobsagora` | Todos | 404 Not Found |
| `/jobsagora` | Todos | 404 Not Found |

## 📝 Observações

A documentação oficial em https://docs.holdworks.ai/ menciona:
- Header: `Authorization: Bearer <api_key>`
- Mas na prática, o único que funciona é: `x-api-key: <api_key>`

O endpoint `/api-key/jobs/data` foi descoberto através de testes e é o único que retorna dados válidos.

## 🔍 Testes Realizados

```bash
# Teste que FUNCIONA ✅
curl "https://api.holdworks.ai/api-key/jobs/data" \
  -H "x-api-key: 4e20f4c2-6f84-49e7-9ab9-e27d6930a13a"

# Resultado: 148KB de dados JSON com 20 jobs
```

## 📊 Dados Retornados

- **São Paulo**: 20 jobs
- **Porto Alegre**: 20 jobs
- Estrutura completa com: id, code, title, type, customerName, etc.

---

**Status**: ✅ API funcionando perfeitamente com o endpoint `/api-key/jobs/data`
**Última atualização**: 10/12/2025
