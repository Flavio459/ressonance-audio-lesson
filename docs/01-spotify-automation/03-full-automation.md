# Automação Full-Stack: n8n + OpenAI + Spotify

## Overview

Para **automação completa** (criação + geração + publicação), use stack de IA.

```
Fonte de Conteúdo
(Reddit, Blog, RSS)
    ↓
[n8n] Orquestração
    ↓
[OpenAI] LLM gera script
    ↓
[ElevenLabs] TTS (síntese de voz)
    ↓
[Podbean] Hospedagem
    ↓
[Spotify] Publicação via feed RSS
```

**Resultado**: Podcast 100% automatizado, criado por IA.

---

## Stack Recomendado

| Componente | Ferramenta | Preço | Razão |
|---|---|---|---|
| **Hospedagem** | Podbean | R$50-150/męs | Feed RSS nativo, integração Spotify |
| **Orquestração** | n8n (Self-Hosted) | R$0 (VPS ~R$20/m) | Open-source, controle total |
| **LLM** | OpenAI (GPT-4o) | R$10-50/m | Estado-da-arte PT-BR |
| **TTS** | ElevenLabs | R$50-150/m | Vozes naturais PT-BR, 2 locutores |
| **Monitoração** | Sentry | R$0-100/m | Alertas de falhas |

**Custo total**: R$200-500/męs

---

## Arquitetura Detalhada

### Passo 1: Fonte de Conteúdo

**Opção A: Reddit**
```python
# n8n webhook
Sub reddit: r/SeuTopico
    → Top posts do dia
    → Filtra por engagement
    → Pasar para OpenAI
```

**Opção B: Blog/RSS**
```
Seu blog RSS
    → n8n pulsa a cada 6h
    → Novos posts detectados
    → Pasar para OpenAI
```

**Opção C: API Customizada**
```
Seu banco de dados
    → Webhooks n8n
    → Gatilhos customizados
    → Pasar para OpenAI
```

### Passo 2: LLM (OpenAI GPT-4o)

```javascript
// Prompt para gerar roteiro de podcast
const systemPrompt = `
Você é um roteirista de podcast profissional em PT-BR.
Crie um roteiro para podcast de 8-12 minutos sobre: [TÓPICO]

Formatao:
1. Introdução (1 min)
2. Corpo (6-8 min) com 3 pontos principais
3. Conclusão (1-2 min)

Tom: Profissional, engajador, conversacional.
Não use música ou éfitos sonoros.
`

const response = await openai.createChatCompletion({
  model: 'gpt-4o',
  messages: [{ role: 'system', content: systemPrompt }],
  max_tokens: 1500
})

return response.choices[0].message.content
```

**Saída**: Roteiro estruturado pronto para TTS.

### Passo 3: TTS (ElevenLabs)

```python
# Gera áudio a partir do roteiro
import elevenlabs

# 2 locutores alternados
rotas_pt_br = ['George (Locutor 1)', 'Bella (Locutor 2)']

audio_buffer = elevenlabs.generate(
  text=roteiro,
  voice=rotas_pt_br[0],  # Alterna locutores
  model="eleven_multilingual_v2"
)

# Salva arquivo WAV
with open('episodio.wav', 'wb') as f:
    f.write(audio_buffer)
```

**Saída**: Arquivo de áudio (WAV/MP3) pronto.

### Passo 4: Upload Podbean (n8n)

```javascript
// Upload do áudio para Podbean
const podbean_response = await fetch(
  'https://api.podbean.com/v1/episodes',
  {
    method: 'POST',
    headers: {
      'Authorization': `Bearer ${PODBEAN_TOKEN}`,
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      title: titulo_gerado_pela_ia,
      description: descricao_ia,
      content_type: 'audio/mp3',
      logo_image_url: imagem_ia,
      media_url: arquivo_audio_url,
      publish_time: Math.floor(Date.now() / 1000) // Agora
    })
  }
)
```

### Passo 5: Sincronização Spotify

```
Podbean publica episódio
    ↓
Feed RSS atualizado (automático)
    ↓
Spotify pulsa feed (~5 min)
    ↓
Episódio aparece em Spotify
```

---

## Fluxo n8n Completo

```
[Trigger: Webhook ou Schedule]
    ↓
[HTTP Request: Buscar conteúdo de Reddit]
    ↓
[Format: Estruturar dados]
    ↓
[OpenAI: Gerar roteiro]
    ↓
[Decision: Qualidade OK?]
    ├─ SIM → Continuar
    └─ NÃO → Alertar, tentar novamente
    ↓
[ElevenLabs: Gerar áudio (TTS)]
    ↓
[S3 ou Google Cloud: Hospedar áudio]
    ↓
[Podbean API: Upload + Publica]
    ↓
[Log: Registrar sucesso]
    ↓
[Notificação: Slack/Email]
```

---

## Setup Passo a Passo

### 1. Instalar n8n (Self-Hosted)

```bash
# Usando Docker
docker run -it --rm \
  -p 5678:5678 \
  -e N8N_HOST=seu-vps.com \
  n8nio/n8n

# Ou VPS (Ubuntu)
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo npm install -g n8n
n8n start
```

### 2. Configurar Integradores no n8n

**OpenAI**:
```
Credenciais → OpenAI → Cole API Key
```

**ElevenLabs**:
```
Credenciais → ElevenLabs → Cole API Key
```

**Podbean**:
```
Credenciais → Podbean OAuth2 → Autorizar
```

### 3. Criar Workflow

```
1. N8N UI: http://seu-vps.com:5678
2. "New Workflow"
3. Arraste nodes (HTTP, OpenAI, ElevenLabs, Podbean)
4. Conecte conforme fluxo acima
5. Teste com "Execute Workflow"
6. Ativação: "Active" toggle
```

---

## Exemplos de Casos de Uso

### Caso 1: Reddit → Podcast Automático

```
Trigger: Diário às 8h
Ação: Pega top post de r/AskReddit
Prompt: "Converta este post de Reddit em episódio de podcast com 2 locutores"
Saída: Episódio publica em Spotify
```

### Caso 2: Blog + Podcast

```
Trigger: Novo post publicado no seu blog
Ação: Lê o artigo inteiro
Prompt: "Resuma este artigo e crie roteiro de podcast"
Saída: Episódio de 10 min aparece em Spotify
```

### Caso 3: Resumo de Notícias

```
Trigger: Diário às 7h
Ação: Agrega top notícias de BBC/Reuters (RSS)
Prompt: "Crie podcast de 5 min com top 3 notícias do dia"
Saída: "Daily News Podcast" publica automático
```

---

## Monitoramento e Alertas

### Falhas Comuns e Soluções

| Falha | Causa | Solução |
|---|---|---|
| "Rate limit exceeded" | Muitos requests OpenAI | Aumentar delay entre chamadas |
| "TTS timeout" | Áudio muito longo | Limitar roteiro a 1500 caracteres |
| "Podbean 401" | Token expirado | Renovar OAuth2 |
| "Feed RSS não atualiza" | Spotify ainda sincronizando | Aguardar 10 min |

### Alertas Recomendados

```json
{
  "slack_webhook": "https://hooks.slack.com/...",
  "alerts": [
    {
      "event": "workflow_failed",
      "severity": "critical",
      "message": "Podcast automation falhou - revisar logs"
    },
    {
      "event": "cost_exceeded",
      "severity": "warning",
      "threshold": "R$500/męs"
    }
  ]
}
```

---

## Custo-Benefício

**Setup Inicial**: ~R$500 (VPS, configuração)
**Custo Mênés**: R$200-500
**Podcasts/Mês**: 20-60 (1-2 por dia)
**Custo por Episódio**: R$3-25
**ROI**: Break-even em 2-4 meses com monetização

---

## Recomendação Executiva

Use este stack se:
- ✅ Quer criar 15+ episódios/męs
- ✅ Tem orçamento de R$500+/męs
- ✅ Quer automatização completa (criação + publicação)
- ✅ Tem equipe técnica para manutenha

Não use se:
- ❌ Produz <5 episódios/męs
- ❌ Quer conteúdo 100% humano
- ❌ Sem know-how técnico

---

**Versão**: 1.0 | **Última atualização**: Janeiro 2026
