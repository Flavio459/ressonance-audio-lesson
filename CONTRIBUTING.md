# Guia de Contribuição

> Bem-vindo! Este repositório é colaborativo. Suas contribuições ajudam a comunidade.

## Tipos de Contribuição

### 1. Contribuições de Documentação

**O que vale**:
- Novos documentos sobre automação de podcasts
- Casos de uso reais (com permissão)
- Correção de erros ou desatualização
- Melhorias em clareza e estrutura
- Tradução para outros idiomas

**Formato**:
- Markdown (.md)
- Estrutura: Intro → Conceito → Passo a Passo → Exemplo → Recursos
- Máximo: 2000 palavras
- Mínimo: 300 palavras

---

### 2. Contribuições de Código

**O que vale**:
- Scripts úteis (validadores, exportadores)
- Templates n8n, flows, configurações
- Ferramentas de automação
- Integradores com APIs

**Pasta**: `scripts/` ou `templates/`
**Linguagem**: Python, JavaScript, JSON preferencialmente
**Documentação**: Obrigatório (README no folder)

---

### 3. Contribuições de Casos de Estudo

**O que vale**:
- Podcasts reais com métricas (permissão do autor)
- Workflows customizados que funcionaram
- Lições aprendidas
- ROI alcançado

**Pasta**: `case-studies/`
**Formato**: Markdown com:
- Título
- Contexto (quem, o quê)
- Estratégia usada
- Métricas/Resultados
- Lições aprendidas
- Contato (opcional)

---

## Processo de Contribuição

### Passo 1: Fork do Repositório

```bash
git clone https://github.com/[seu-username]/ressonance-audio-lesson.git
cd ressonance-audio-lesson
```

### Passo 2: Criar Branch

**Nomeclatura**:
- Documentação: `docs/topico-nome`
- Código: `feature/descricao-curta`
- Correção: `fix/descricao-curta`
- Caso de uso: `case-study/nome-podcast`

**Exemplo**:
```bash
git checkout -b docs/youtube-to-podcast-automation
```

### Passo 3: Fazer Alterações

**Para Documentação**:
```bash
# Crie arquivo no local correto
touch docs/02-podcast-workflow/seu-topico.md

# Edite com editor de sua preferência
vim docs/02-podcast-workflow/seu-topico.md
```

**Para Código**:
```bash
# Crie arquivo em scripts/ ou templates/
touch scripts/seu-script.py

# Inclua docstring/comentarios
# Crie README.md explicando o script
```

### Passo 4: Commit

**Mensagem de Commit**:
```
[tipo]: descrção curta

Descrever o quê foi feito e por quê.

Typo: 
- docs: documentação
- feat: novo recurso
- fix: correção
- script: novo script
- case: novo caso de estudo
```

**Exemplos**:
```bash
git add docs/02-podcast-workflow/youtube-automation.md
git commit -m "docs: guia de automação YouTube para podcast

Descreve passo a passo como integrar YouTube com n8n e Spotify.
Inclui exemplos de fluxos e métricas."

---

git add scripts/youtube-downloader.py
git commit -m "script: downloader de vídeos YouTube com metadados

Permite download automático de vídeos YouTube com extração
de título, descrição e miniaturas."
```

### Passo 5: Push e Pull Request

```bash
git push origin docs/youtube-to-podcast-automation
```

Vá para GitHub e clique "Create Pull Request"

**Descrição do PR**:
```
## Descrição

O que esta PR faz e por quê.

## Tipo de Mudança

- [ ] Documentação
- [ ] Novo script
- [ ] Correção
- [ ] Caso de estudo
- [ ] Outro (descreva)

## Checklist

- [x] Testei o conteúdo/código
- [x] Segui o padrão de nomenclatura
- [x] Incluí exemplos e referências
- [ ] Permissões obtidas (se case study)

## Links Relacionados

- Relacionado com issue #123
- Baseado em pesquisa sobre X
```

### Passo 6: Review e Merge

- Especialista em conteúdo revisará em 24-48h
- Pode solicitar mudanças
- Após aprovação, será mergado

---

## Padrões de Escrita

### Estrutura de Documento

```markdown
# TÍtulo Principal

## Overview / Visão Geral

Uma linha (max 100 caracteres) com o essencial.

## Seção 1: Conceito

Descreva o conceito fundamental.

### Subsecção 1.1

Mais detalhes.

## Seção 2: Passo a Passo

```bash
# Códigos ou comandos
```

## Seção 3: Exemplos

| Campo | Valor |
|---|---|
| Exemplo | Demonstração |

## Seção 4: Recursos Adicionais

- [Link 1](url)
- [Link 2](url)

---

**Versão**: 1.0 | **Última atualização**: YYYY-MM-DD
```

### Estilo

- **Conciso**: Evite parágrafos muito longos (máx 3 linhas)
- **Prático**: Pref irá exemplos à teoria
- **Claro**: Use headings, listas, tabelas
- **Link**: Referencie outros documentos quando apropriado
- **PT-BR**: Portuguese brasileiro, mas com termos técnicos em inglês

---

## Checklist de Qualidade

Antes de submeter, verifique:

- [ ] **Ortografia**: Sem erros de ortografia
- [ ] **Estrutura**: Segue padrão proposto
- [ ] **Exemplos**: Inclui pelo menos 1 exemplo prático
- [ ] **Links**: Todos os links estão válidos
- [ ] **Versão**: Data e versão atualizadas no footer
- [ ] **Código**: Testado (se script)
- [ ] **Referências**: Créditos dados (se baseado em source externo)
- [ ] **Sem Plag**: Conteúdo original ou com citação

---

## Perguntas Frequentes

### Posso contribuir anonimamente?

Sim! Use um alias no GitHub ou crie uma conta apenas para contribuir.

### Como creditar meu caso de estudo?

Adicione seção "Sobre o Autor" no final do documento com:
- Nome/Username
- Redes sociais (opcional)
- Website (opcional)
- Email (opcional)

### Posso traduzir documentação existente?

Sim! Crie uma pasta `docs/[lang]` (ex: `docs/en/`) e envie PR.

### Quanto de tempo leva ser mergado?

- Documentação: 24-48h
- Script: 48-72h (requer teste)
- Caso de estudo: 24h

---

## Contato

Dúvidas? Abra uma issue com tag `[question]`.

---

**Obrigado por contribuir! 🉏**
