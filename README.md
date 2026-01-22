🌤️ MeteoroBR: Chatbot de Clima Inteligente (Telegram + n8n)

Este projeto implementa um chatbot de clima no Telegram, desenvolvido no n8n, que consulta a OpenWeather API para retornar a temperatura atual de uma cidade brasileira informada pelo usuário. O bot utiliza Inteligência Artificial (Google Gemini) para humanizar as respostas e possui um sistema de fallback para garantir o funcionamento mesmo sem IA.

📌 Funcionalidades

Integração Nativa: Conectado diretamente com o Telegram Bot API.

Dados em Tempo Real: Consulta climática via OpenWeather.

NLP (Processamento de Linguagem Natural): Uso de IA Gemini para respostas amigáveis e naturais.

Normalização Automática: Validação de entrada e tratamento de acentos/espaços.

Segurança Territorial: Filtro de validação para cidades apenas dentro do Brasil (BR).

Resiliência Total: Sistema de fallback determinístico caso a IA falhe ou as credenciais não estejam configuradas.

📂 Estrutura do Workflow

O fluxo principal do workflow segue estas etapas lógicas:

Telegram Trigger: Inicia o fluxo ao receber mensagens enviadas ao bot.

Configurações Iniciais: Centraliza a chave da API (OpenWeather) para fácil manutenção e segurança.

Captura e Formatação: Cria a variável queue e normaliza o texto (remove acentos, espaços e converte para minúsculas).

OpenWeather HTTP Request: Realiza a chamada técnica para a API de clima usando Query Parameters.

IF Sucesso: Verifica se a cidade foi encontrada (Status 200) e se pertence ao território brasileiro (BR).

Extração e Fallback: Prepara a mensagem padrão arredondada e determinística.

IA Gemini: Refina a mensagem técnica em uma saudação calorosa (se configurado).

Enviar Resposta: Entrega a mensagem final ao usuário via Telegram, tratando possíveis tags incompatíveis.

🚀 Como importar no n8n

Acesse o painel do seu n8n.

Vá em Workflows -> Import from file.

Selecione o arquivo workflow-telegram-chatbot.json deste repositório.

Clique em Save.

🔐 Configuração das Credenciais

1. Telegram Bot (via BotFather)

Para criar seu bot e obter o token:

No Telegram, converse com o @BotFather.

Envie o comando /newbot e siga as instruções para definir nome e username.

Copie o API Token fornecido.

No n8n, vá em Credentials -> Add Credential -> Telegram API.

Preencha o campo Access Token e salve. Vincule esta credencial aos nós de Trigger e Envio.

2. OpenWeather API

Crie uma conta em OpenWeatherMap.

Gere uma API Key no painel da sua conta (My API Keys).

No n8n, abra o nó "Configurações Iniciais" e substitua o valor SUA_API_AQUI pela sua chave real.

3. Google Gemini (Opcional)

Obtenha sua chave de API no Google AI Studio.

No n8n, crie uma credencial do tipo Google Gemini(PaLM) API.

Insira sua chave e associe a credencial ao nó "Google Gemini Chat Model".

⚙️ Variáveis Esperadas

Variável

Descrição

OPENWEATHER_API_KEY

Chave de acesso à API OpenWeather

TELEGRAM_BOT_TOKEN

Token de autenticação do Bot Telegram

🌐 Publicar o workflow (Obrigatório)

Para que o bot funcione em tempo real (webhook):

Abra o workflow no n8n.

No canto superior direito, ative a chave Active (ou clique em Publish).

Certifique-se de que o workflow aparece com o status "Active" na sua lista.

🎮 Como usar o chatbot

Inicie uma conversa com seu bot no Telegram e envie o nome da cidade:

Formato recomendado: Cidade, UF ou apenas Cidade.

Exemplos: Londrina, PR, São Paulo.

Exemplos de Resposta:

Sucesso: "Bom dia! Em Londrina, o tempo está ensolarado e a temperatura registra 26°C. Um dia agradável! 🌤️"

Erro: "❌ Cidade não encontrada ou fora do Brasil. Use o formato Cidade, UF (ex.: São Paulo, SP)."

🛠️ Solução de Problemas (Troubleshooting)

Erro 401 (Unauthorized): Verifique se o token da OpenWeather no nó de "Configurações Iniciais" está correto.

Erro 404 (Not Found): O bot está configurado apenas para o Brasil. Verifique se a cidade informada é brasileira.

O bot não responde: Verifique se o workflow está em modo Active. No modo "Test", ele só responde enquanto você clica manualmente em executar.

✅ Observações Finais

Segurança: O arquivo JSON exportado não contém chaves de API reais por segurança.

Desenvolvido como critério de avaliação para a Pós-Graduação - 2026.