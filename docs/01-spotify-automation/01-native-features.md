# Funcionalidades Nativas de Automação

## 1. Agendamento de Episódios

### Como Funciona

```
1. Acesse Spotify for Creators (creators.spotify.com)
2. Clique em "Novo Episódio" ou "Upload"
3. Selecione "Data de publicação"
4. Escolha "Programar" (em vez de "Publicar agora")
5. Configure data e horário
6. Confirmar
```

### Características

| Aspecto | Detalhes |
|---|---|
| **Antecedência** | Até anos de antecipação |
| **Fuso horário** | Spotify automaticamente se adapta |
| **Revisão** | Pode editar ou reverter para rascunho antes da publicação |
| **Notificação** | Seguidores recebem notificação automática |
| **Sincronização** | Publica em Spotify simultaneamente (não em outras plataformas) |

### Limitação

📍 **Manual**: Cada episódio precisa ser feito individualmente. Não é automação de processo.

### Use Case

**Ideal para**: Criadores que fazem upload 1-2x/semana com conteúdo planejado.

---

## 2. Broadcast-to-Podcast (B2P)

### O Que É

Automatiza conversão de **transmissões ao vivo** em episódios de podcast.

```
Transmissão ao Vivo (YouTube, Facebook, etc)
    ↓ [Megaphone B2P]
Download automático
    ↓
Remoção de anúncios/pausas
    ↓
Geração automática de metadados
    ↓
Publicação em Spotify + Apple + Google
```

### Funcionalidades

- ✅ Download automático da transmissão
- ✅ Remoção de silêncios e cenas paradas
- ✅ Marcação automática de segmentos
- ✅ Geração de metadados (título, descrição, imagem)
- ✅ Publicação multi-plataforma

### Plataformas Suportadas

| Fonte | Status |
|---|---|
| **YouTube Live** | ✅ Completo suporte |
| **Facebook Live** | ✅ Completo suporte |
| **Periscope (X)** | ✅ Suporte limitado |
| **LinkedIn Live** | ❓ Verificar documentação Megaphone |
| **Twitch** | ❓ Não confirmado |

### Plataforma: Megaphone

- **Proprietário**: Spotify
- **Preço**: Começa ~R$500/mês (pro)
- **Setup**: 1-2 horas integração
- **ROI**: Econômico para creators com 1+ transmissão/semana

### Use Case

**Ideal para**: 
- Streamers convertendo Twitch → Podcast
- Criadores de YouTube com conteúdo ao vivo
- Podcasts ao vivo em múltiplas plataformas

---

## 3. Feeds Sincronizados

### O Que É

Mescla episódios de múltiplas fontes (Patreon, Substack, Spotify) **sem duplicatas**.

```
Episódio Gratuito (Spotify)
    ↓ [Feed Sincronizado]
Episódio Premium (Patreon)
    ↓
Ouça assinante: versão premium primeiro
Ouaça genérico: versão gratuita
```

### Características

| Funcionalidade | Detalhe |
|---|---|
| **Mesclagem** | Spotify mescla episódios de múltiplas fontes |
| **Personalização** | Ouvinte premium vê episódios premium primeiro |
| **Dedução** | Evita duplicatas automáticamente |
| **Suporte** | Patreon, Substack, Supporting Cast, Supercast |

### Configuração

```
Spotify for Creators
    → Episódios
    → Feeds Sincronizados
    → Adicionar fonte
    → Autenticar (Patreon, Substack, etc)
    → Sincronizar
```

### **LIMITAÇÃO CRÍTICA**

📑 **Feeds sincronizados NÃO funcionam para podcasts hospedados nativamente no Spotify for Creators.**

**Quando funciona**: 
- Podcast hospedado em plataforma parceira (Libsyn, Podbean, etc)
- Feeds premium vindo de Patreon, Substack, etc

**Quando NÃO funciona**:
- Podcast uploadado diretamente no Spotify for Creators
- Tentando sincronizar feeds internos

### Use Case

**Ideal para**: 
- Creators com modelo de receita mixto (gratuito + premium)
- Podcasts que usam Patreon ou Substack
- Distribuição omnicanal

---

## Comparação: Qual Usar?

```
Você faz...

┌─ Transmissões ao vivo regularmente?
│  → Use B2P (Megaphone)
│
├─ Upload manual 1-2x/semana?
│  → Use Agendamento nativo
│
├─ Modelo de monetização gratuito + premium?
│  → Use Feeds Sincronizados (se em plataforma parceira)
│
└─ Quer automação completa (criação + publicação)?
   → Veja 02-rss-feeds.md ou 03-full-automation.md
```

---

## Recursos Adicionais

- [Spotify for Creators - Suporte Oficial](https://support.spotify.com/br-pt/creators/)
- [Megaphone (B2P) - Documentação](https://megaphone.fm/)
- [Feeds Sincronizados - Guia](https://support.spotify.com/br-pt/creators/article/synced-feeds/)

---

**Versão**: 1.0 | **Última atualização**: Janeiro 2026
