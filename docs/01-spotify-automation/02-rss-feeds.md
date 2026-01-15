# Arquitetura Feed RSS → Spotify

## Overview

O caminho mais **viável para automação** de podcasts no Spotify é usar uma plataforma de hospedagem externa com **Feed RSS sincronizado**.

```
Você publica episódio
    ↓
[Plataforma de Hospedagem: Podbean, Libsyn, Spreaker]
    ↓
Gera Feed RSS
    ↓
Spotify lê automaticamente (~5 min)
    ↓
Episódio aparece em Spotify
```

---

## Plataformas Recomendadas

### 1. Anchor (Spotify)

| Aspecto | Detalhe |
|---|---|
| **Preço** | Gratuito |
| **Distribuição** | Spotify, Apple, Google, Amazon automático |
| **Hospedagem** | Inclusa |
| **Feed RSS** | Nativo |
| **Limitação** | Feeds sincronizados não compatíveis |
| **Ideal para** | Iniciantes, máximo ROI |

**Setup**:
```
1. Acesse anchor.fm
2. "Criar novo podcast"
3. Upload de episódios
4. Distribuição automática em 24-48h
```

---

### 2. Podbean

| Aspecto | Detalhe |
|---|---|
| **Preço** | Freemium (R$50-150/mês) |
| **Hospedagem** | Inclusa |
| **Feed RSS** | Sim, com sincronização auto |
| **Agendamento** | Integrado |
| **Analytics** | Avançados |
| **Monetização** | Patreon integrado |
| **Ideal para** | Creators com crescimento e conteúdo plástico |

**Como configurar Spotify**:
```
1. Gere feed RSS no Podbean
2. Vá para Spotify for Creators
3. "Reivindicar seu podcast"
4. Cole URL do feed RSS
5. Sincronização a cada ~5 minutos
```

---

### 3. Libsyn

| Aspecto | Detalhe |
|---|---|
| **Preço** | Pago (R$150-400/mês) |
| **Hospedagem** | Inclusa |
| **Feed RSS** | Nativo de alta qualidade |
| **Agendamento** | Máximo avançado |
| **API** | Disponível |
| **Ideal para** | Profissionais, agendamento complexo |

**Vantagem**: API aberta permite integrações customizadas.

---

### 4. Spreaker

| Aspecto | Detalhe |
|---|---|
| **Preço** | Freemium (R$100-200/mês) |
| **Hospedagem** | Inclusa |
| **Live Streaming** | Integrado |
| **Feed RSS** | Sim |
| **Ideal para** | Creators que combinam podcast + livestream |

---

## Arquitetura Recomendada

### Path: Podbean + Spotify for Creators

```
┌─────────────────────────────────┐
│ 1. Seu Fluxo de Produção          │
│ (Criação/Edição de Áudio)      │
└───────╌────────────────────────┘
              │
          Upload
              │
┌─────────────────────────────────┐
│ 2. Podbean                        │
│ - Hospedagem                     │
│ - Feed RSS gerado autom.         │
│ - Metadados                      │
└──────╌─────────────────────────┘
              │ RSS
              │ (Pull a cada ~5 min)
              │
┌─────────────────────────────────┐
│ 3. Spotify for Creators           │
│ - Lê feed RSS                     │
│ - Sincroniza automaticamente      │
└──────╌─────────────────────────┘
              │
          Publica
              │
┌─────────────────────────────────┐
│ 4. Spotify (Ouvintes)            │
└─────────────────────────────────┘
```

**Tempo total**: Upload → Spotify: ~5-10 minutos

---

## Passo a Passo: Configurar Podbean + Spotify

### Passo 1: Criar Podcast no Podbean
```
1. Acesse podbean.com
2. "Create New Podcast"
3. Nome, categoria, descrição, arte
4. Ativação
```

### Passo 2: Obter Feed RSS
```
1. Podcasts → [Seu Podcast]
2. "Distribução"
3. Copie "RSS Feed URL"
4. Formato: https://myfeed.podbean.com/feed.xml
```

### Passo 3: Reivindicar no Spotify
```
1. Acesse creators.spotify.com
2. "Reivindicar seu podcast"
3. Cole URL do RSS do Podbean
4. Valide (Spotify verifica)
5. Pronto! Sincroniza a cada ~5 min
```

### Passo 4: Upload de Episódios
```
1. Podbean: "Upload Episode"
2. Título, descrição, arquivo de áudio
3. Publicação (agora ou programada)
4. Salvar
5. ~5-10 min depois: Aparece em Spotify
```

---

## Automação Adicional: Agendamento

### Recurso: Agendamento de Episódios

Todas as plataformas permitem **agendamento integrado**:

```
Podbean (ou similar)
    → "Schedule for later"
    → Data/Hora
    → Salvar
    ↓
Na data programada:
    → Publica automáticamente
    → Feed RSS atualiza
    → Spotify sincroniza
```

**Resultado**: Publicação 100% automática sem intervenção.

---

## Monitoração

### Checklist Pós-Upload

- [ ] Episódio publica em Podbean
- [ ] Feed RSS atualizado (verifique XML)
- [ ] Spotify sincronizou (~5-10 min)
- [ ] Metadados corretos (título, arte, descrição)
- [ ] Áudio plays corretamente
- [ ] URL do episódio disponível

### Ferramentas Ãteis

- **Feed RSS Validator**: [feedvalidator.org](https://feedvalidator.org)
- **Spotify API**: Verifique sindicalização de status
- **Podbean Analytics**: Rastreie downloads

---

## Comparação de Preços e Recursos

| Plataforma | Preço | Agendamento | API | Feeds Sincronizados |
|---|---|---|---|---|
| **Anchor** | Gratuito | ❌ Não | ❌ Não | ❌ Não |
| **Podbean** | R$50-150/mês | ✅ Sim | ❌ Não | ✅ Sim (Patreon) |
| **Libsyn** | R$150-400/mês | ✅ Avançado | ✅ Sim | ✅ Sim |
| **Spreaker** | R$100-200/mês | ✅ Sim | ❌ Não | ✅ Limitado |

---

## Recomendação Executiva

**Para maioria dos casos**: **Podbean** oferece melhor balanço custo/benefício.

- Gratuito até R$50/mês
- Agendamento completo
- Integração Spotify perfeita
- Suporte a Patreon (feeds sincronizados)

---

**Versão**: 1.0 | **Última atualização**: Janeiro 2026
