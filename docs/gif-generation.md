# Space Shooter GIF Generation Documentation

## 📖 Visão Geral

O arquivo `Hic-Tayfour-space-shooter.gif` no repositório é gerado automaticamente através de um GitHub Actions workflow que transforma o gráfico de contribuições do GitHub em um jogo de space shooter animado.

## 🤖 Workflow Automático

### Execução Automática
O workflow é executado automaticamente:
- **Diariamente**: Todos os dias à meia-noite (UTC)
- **Automaticamente**: Sempre que o workflow detecta que há mudanças no gráfico de contribuições

### Execução Manual

Para gerar o GIF manualmente:

1. Acesse a aba **Actions** do repositório
2. Clique em **Update Space Shooter GIF** na lista de workflows
3. Clique no botão **Run workflow**
4. Selecione a branch (geralmente `main`)
5. Clique em **Run workflow** novamente

O processo levará alguns minutos e você pode acompanhar o progresso na aba Actions.

## ⚙️ Configuração

### Parâmetros Configuráveis

O workflow pode ser personalizado editando o arquivo `.github/workflows/update-space-shooter-gif.yml`:

#### FPS (Frames Per Second)
Controla a fluidez da animação e o tamanho do arquivo:

```yaml
fps: '15'  # Valor atual
```

- **Valores menores** (10-15): Arquivo menor, animação menos fluida
- **Valores maiores** (20-40): Arquivo maior, animação mais fluida
- **Recomendado**: 15-20 para balancear tamanho e qualidade

#### Estratégia de Ataque
Define o padrão de ataque dos inimigos:

```yaml
strategy: 'random'  # Valor atual
```

Opções disponíveis:
- `random`: Ataques aleatórios (padrão, mais dinâmico)
- `column`: Inimigos atacam por coluna
- `row`: Inimigos atacam por linha

#### Nome do Arquivo
O arquivo é sempre salvo como:

```yaml
output-path: 'Hic-Tayfour-space-shooter.gif'
```

**⚠️ Importante**: Não altere este nome, pois o README.md referencia exatamente este arquivo.

## 🧪 Teste Local

Para gerar o GIF localmente (opcional):

### Pré-requisitos
```bash
# Instalar Python 3.12+
python --version

# Instalar gh-space-shooter
pip install gh-space-shooter
```

### Geração Local
```bash
# Criar token GitHub (necessário apenas uma vez)
# Vá para: https://github.com/settings/tokens
# Crie um token com permissão 'read:user'

# Definir variável de ambiente
export GH_TOKEN=seu_token_aqui

# Gerar GIF
gh-space-shooter Hic-Tayfour \
  --output Hic-Tayfour-space-shooter.gif \
  --strategy random \
  --fps 15

# Verificar o arquivo gerado
ls -lh Hic-Tayfour-space-shooter.gif
```

### Ajustar Parâmetros Localmente
```bash
# FPS mais alto (animação mais fluida, arquivo maior)
gh-space-shooter Hic-Tayfour --fps 30

# FPS mais baixo (animação menos fluida, arquivo menor)
gh-space-shooter Hic-Tayfour --fps 10

# Estratégia diferente
gh-space-shooter Hic-Tayfour --strategy column
```

## 📊 Custos e Tempo de Execução

### Tempo de Execução
- **Tempo estimado**: 2-5 minutos por execução
- **Componentes**:
  - Setup do ambiente: ~1 minuto
  - Geração do GIF: ~1-3 minutos
  - Commit e push: ~10-30 segundos

### Uso do GitHub Actions
- **Execuções programadas**: 1 vez por dia = ~30 execuções/mês
- **Tempo total mensal**: ~60-150 minutos/mês
- **Custo**: Gratuito para repositórios públicos
- **Minutos gratuitos**: 2.000 minutos/mês no plano Free

### Otimização de Custos
O workflow já está otimizado:
- ✅ Usa commit condicional (não commita se não houver mudanças)
- ✅ Timeout de 10 minutos (evita execuções travadas)
- ✅ Execução diária (frequência adequada)

## 🔧 Solução de Problemas

### O GIF não foi gerado
1. Verifique se o workflow foi executado com sucesso na aba Actions
2. Veja os logs do step "Generate Space Shooter GIF"
3. Verifique se há contribuições no gráfico do GitHub

### O GIF está muito grande
1. Reduza o FPS no arquivo de workflow (ex: de 15 para 10)
2. Commit a mudança e execute o workflow manualmente

### O GIF está muito "travado"
1. Aumente o FPS no arquivo de workflow (ex: de 15 para 20)
2. Commit a mudança e execute o workflow manualmente

### Workflow falhou
Causas comuns:
- Token do GitHub expirado ou sem permissões
- Timeout (processo demorou mais de 10 minutos)
- Erro na API do GitHub

Solução:
1. Verifique os logs detalhados no Actions
2. Re-execute o workflow manualmente
3. Se persistir, abra uma issue

## 📚 Recursos Adicionais

- [Repositório gh-space-shooter](https://github.com/czl9707/gh-space-shooter)
- [Documentação GitHub Actions](https://docs.github.com/en/actions)
- [Cron Expression Generator](https://crontab.guru/)

## 🎮 Como Funciona

O GIF é gerado a partir do seu gráfico de contribuições do GitHub:
1. O workflow busca suas contribuições do último ano
2. Cada dia de contribuição vira um "inimigo" no jogo
3. Quanto mais contribuições, mais forte o inimigo
4. Uma nave espacial "destrói" os inimigos seguindo a estratégia escolhida
5. O resultado é salvo como GIF animado

**Duração do GIF**: Determinada automaticamente pela quantidade de contribuições. Quanto mais contribuições, mais longo o jogo e maior o GIF.
