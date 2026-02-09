# Códigos de Erro WhatsApp Cloud API - Português BR

[![JSON](https://img.shields.io/badge/JSON-Lista%20Completa-green)](errors.json)
[![WhatsApp](https://img.shields.io/badge/WhatsApp-Cloud%20API-25D366?logo=whatsapp)](https://developers.facebook.com/docs/whatsapp/cloud-api)
[![Português](https://img.shields.io/badge/Idioma-Portugu%C3%AAs%20BR-blue)](README.md)

Lista completa de códigos de erro da **WhatsApp Cloud API** traduzidos para **português brasileiro** (pt-br) em formato JSON.

## Por que este projeto existe?

Ao desenvolver integrações com a WhatsApp Cloud API, encontrar os códigos de erro traduzidos e organizados em um único arquivo é difícil. Este repositório resolve esse problema oferecendo todos os error codes da API do WhatsApp Business em português, prontos para uso em seus projetos.

## O que está incluído

- **40+ códigos de erro** da WhatsApp Cloud API
- Tradução completa para português brasileiro
- Estrutura JSON organizada e fácil de usar
- Campos detalhados: código, título, mensagem, detalhes e resolução
- Pronto para integração em sistemas de tratamento de erros

## Estrutura dos dados

Cada erro contém as seguintes informações:

```json
{
  "code": 0,
  "title": "Exceção de Autenticação",
  "message": "Não foi possível autenticar o usuário do app.",
  "details": "Geralmente significa que o token expirou ou o usuário revogou o acesso.",
  "resolution": "Gere um novo token de acesso."
}
```

### Campos

| Campo        | Descrição                                  |
| ------------ | ------------------------------------------ |
| `code`       | Código numérico do erro retornado pela API |
| `title`      | Título descritivo do erro                  |
| `message`    | Mensagem de erro em português              |
| `details`    | Explicação detalhada sobre a causa do erro |
| `resolution` | Solução sugerida para resolver o problema  |

## Como usar

### Uso direto via URL

Você pode consumir o JSON diretamente via GitHub:

```javascript
// JavaScript/Node.js
const response = await fetch(
  'https://raw.githubusercontent.com/AlexSzefezuk/meta-whatsapp-error-codes-pt-br/main/errors.json'
)
const errorCodes = await response.json()
```

```python
# Python
import requests

response = requests.get('https://raw.githubusercontent.com/AlexSzefezuk/meta-whatsapp-error-codes-pt-br/main/errors.json')
error_codes = response.json()
```

### Clonar o repositório

```bash
git clone https://github.com/AlexSzefezuk/meta-whatsapp-error-codes-pt-br.git
```

### Download direto

Baixe o arquivo [errors.json](errors.json) e adicione ao seu projeto.

## Exemplos de implementação

### Buscar erro por código

```javascript
function getErrorByCode(errorCode) {
  const error = errorCodes.errors.find(e => e.code === errorCode)
  return error || { message: 'Erro desconhecido' }
}

// Exemplo de uso
const error = getErrorByCode(131047)
console.log(error.message) // "Mensagem de reengajamento necessária."
console.log(error.resolution) // "Envie um template para abrir uma nova janela de 24h."
```

### Sistema de tratamento de erros

```javascript
async function sendWhatsAppMessage(data) {
  try {
    const response = await whatsappAPI.send(data)
    return response
  } catch (error) {
    const errorInfo = getErrorByCode(error.code)

    console.error(`Erro ${errorInfo.code}: ${errorInfo.title}`)
    console.error(`Mensagem: ${errorInfo.message}`)
    console.error(`Solução: ${errorInfo.resolution}`)

    // Seu tratamento customizado aqui
    handleWhatsAppError(errorInfo)
  }
}
```

## Principais categorias de erros

### Autenticação e Permissões

- Código 0: Exceção de Autenticação
- Código 190: Token de acesso expirado
- Código 3: Permissão ausente
- Código 10: Permissão negada

### Limites e Rate Limiting

- Código 4: Limite de chamadas de API
- Código 80007: Limite de taxa da WABA
- Código 130429: Limite de throughput
- Código 131048: Limite de spam
- Código 131056: Limite de emparelhamento

### Templates

- Código 132000: Número incorreto de parâmetros
- Código 132001: Template não existe
- Código 132012: Template pausado
- Código 132015: Template desabilitado

### Mensagens e Mídia

- Código 131026: Mensagem não entregue
- Código 131047: Janela de 24h expirada
- Código 131051: Erro de download de mídia
- Código 131052: Erro de upload de mídia
- Código 131053: Tipo de arquivo não suportado

### Conta e Bloqueios

- Código 368: Bloqueado temporariamente
- Código 131031: Conta bloqueada
- Código 131042: Problema de pagamento

## Recursos relacionados

- [Documentação oficial WhatsApp Cloud API](https://developers.facebook.com/docs/whatsapp/cloud-api)
- [Error Codes Reference (Meta)](https://developers.facebook.com/docs/whatsapp/cloud-api/support/error-codes)
- [WhatsApp Business API](https://business.whatsapp.com/products/business-platform)

## Contribuindo

Encontrou algum erro de tradução ou quer adicionar mais códigos? Contribuições são bem-vindas!

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/nova-traducao`)
3. Commit suas mudanças (`git commit -m 'Adiciona novos códigos de erro'`)
4. Push para a branch (`git push origin feature/nova-traducao`)
5. Abra um Pull Request

## Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## Palavras-chave

whatsapp api, whatsapp cloud api, whatsapp business api, códigos de erro whatsapp, error codes whatsapp, whatsapp errors português, meta whatsapp api, waba errors, whatsapp api brasil, whatsapp error codes pt-br, tradução whatsapp api, lista erros whatsapp

---

Desenvolvido para a comunidade brasileira de desenvolvedores WhatsApp 🇧🇷

Se este projeto foi útil, deixe uma ⭐ no repositório!
