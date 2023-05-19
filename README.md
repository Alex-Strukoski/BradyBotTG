# BradyBot

Um chatbot para Telegram que se integra com as APIs do OpenAI para fornecer serviços de provedores de internet. Pronto para usar com configuração mínima necessária.

## Screenshots

![BradyBot conversando com um usuário sobre planos de internet](screenshots/bradybot1.png)
![BradyBot gerando uma fatura para um usuário](screenshots/bradybot2.png)

## Recursos

- Suporte a markdown nas respostas
- Resetar a conversa com o comando /reset
- Indicador de digitação enquanto gera uma resposta
- O acesso pode ser restrito especificando uma lista de usuários permitidos
- Suporte a Docker e Proxy (NOVO!)
- Geração de imagem usando DALL·E via o comando /image (NOVO!)
- Transcrição de áudio e vídeo usando Whisper (pode requerer ffmpeg) (NOVO!)
- Resumo automático da conversa para evitar uso excessivo de tokens (corrige #34) (NOVO!)
- Suporte a chat em grupo com consultas inline
- Para usar esse recurso, habilite as consultas inline para o seu bot no BotFather via o comando /setinline (NOVO!)
- Rastreamento de uso de tokens por usuário (armazenado em /token_usage/user_id.json) - por @AlexHTW (NOVO!)
- Obter estatísticas pessoais de uso de tokens e custo por dia/mês via o comando /stats - por @AlexHTW (NOVO!)
- Palavra-chave de gatilho para chat em grupo - por @tracking

## Pré-requisitos

- Python 3.10+ e Pipenv
- Um bot do Telegram e seu token (veja o tutorial)
- Uma conta do OpenAI (veja a seção de configuração)

## Começando

### Configuração

Personalize a configuração copiando .env.example e renomeando-o para .env, então edite os parâmetros como desejado:

OPENAI_API_KEY= "SUA_CHAVE_DA_API_DO_OPENAI"
TELEGRAM_BOT_TOKEN= "SEU_TOKEN_DO_BOT_DO_TELEGRAM"
# Parâmetros opcionais
ALLOWED_TELEGRAM_USER_IDS= "USER_ID_1,USER_ID_2,..." # Padrão é "*" (todos)
PROXY= "SEU_PROXY" # e.g. "http://localhost:8080", padrão é nenhum
ASSISTANT_PROMPT= "Prompt personalizado" # Padrão é "Você é um assistente útil."
SHOW_USAGE=true # Padrão é false
MAX_TOKENS=2000 # Padrão é 1200
MAX_HISTORY_SIZE=15 # Padrão é 10
MAX_CONVERSATION_AGE_MINUTES=120 # Padrão é 180 (3h)
VOICE_REPLY_WITH_TRANSCRIPT_ONLY=false # Padrão é true
N_CHOICES=1 # Padrão é 1
TEMPERATURE=1.0 # Padrão é 0.5
IMAGE_SIZE= "256x256" # Padrão é 512x512
GROUP_TRIGGER_KEYWORD= "@bot" # Padrão é "" (nenhuma palavra-chave requerida)
TOKEN_PRICE=0.002 # Padrão é 0.002, preço atual: https://openai.com/pricing
IMAGE_PRICES= "0.016,0.018,0.02" # Padrão são os preços do OpenAI Dall-E para os tamanhos 256x256,512x512,1024x1024
TRANSCRIPTION_PRICE=0.006 # Padrão é o preço por minuto do OpenAI Whisper de 0.006

OPENAI_API_KEY: Sua chave da API do OpenAI, você pode obtê-la aqui
TELEGRAM_BOT_TOKEN: O token do seu bot do Telegram, obtido usando o BotFather (veja o tutorial)
ALLOWED_TELEGRAM_USER_IDS: Uma lista separada por vírgulas dos IDs dos usuários do Telegram que são permitidos interagir com o bot (use o getidsbot para encontrar seu ID de usuário). Nota: por padrão, todos são permitidos (*)

### Instalação

Instale as dependências usando pipenv:

```bash
pipenv install --dev
```

Ative o ambiente virtual:

```bash
pipenv shell
```
Instale as bibliotecas e dependências:

```bash
pip install -r requirements.txt
```

Execute o bot:

```bash
python main.py
```

Pronto! Agora você pode conversar com o seu bot no Telegram.

## Comandos

/reset - Reinicia a conversa com o bot.
/image - Gera uma imagem a partir de um prompt textual.
/stats - Mostra as estatísticas pessoais de uso de tokens e custo.
/help - Mostra a ajuda sobre como usar o bot.
/help_group_chat - Mostra a ajuda sobre como usar o bot em chats em grupo.

## Créditos

Este projeto foi inspirado pelo chatgpt-telegram-bot¹ criado por n3d1117.
Este projeto é um protótipo de um chatbot para provedores de internet que se integra com as APIs do OpenAI feito pela Bradypus.
