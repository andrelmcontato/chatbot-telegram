🌤️ MeteoroBR: Chatbot de Clima Inteligente (Telegram + n8n)

Este projeto implementa um chatbot de clima no Telegram, desenvolvido no n8n, que consulta a OpenWeather API para retornar a temperatura atual de uma cidade brasileira informada pelo usuário. O bot utiliza Inteligência Artificial (Google Gemini) para humanizar as respostas e possui um sistema de fallback para garantir o funcionamento mesmo sem IA.

📌 Funcionalidades

•	Integração Nativa: Conectado diretamente com o Telegram Bot API.
•	Dados em Tempo Real: Consulta climática via OpenWeather.
•	NLP (Processamento de Linguagem Natural): Uso de IA Gemini para respostas amigáveis e naturais.
•	Normalização Automática: Validação de entrada e tratamento de acentos/espaços.
•	Segurança Territorial: Filtro de validação para cidades apenas dentro do Brasil (BR).
•	Resiliência Total: Sistema de fallback determinístico caso a IA falhe ou as credenciais não estejam configuradas.

📂 Estrutura do Workflow

O fluxo principal do workflow segue estas etapas lógicas:
1.	Telegram Trigger: Inicia o fluxo ao receber mensagens enviadas ao bot.
2.	Configurações Iniciais: Centraliza a chave da API (OpenWeather) para fácil manutenção e segurança.
3.	Captura e Formatação: Cria a variável queue e normaliza o texto (remove acentos, espaços e converte para minúsculas).
4.	OpenWeather HTTP Request: Realiza a chamada técnica para a API de clima usando Query Parameters.
5.	IF Sucesso: Verifica se a cidade foi encontrada (Status 200) e se pertence ao território brasileiro (BR).
6.	Extração e Fallback: Prepara a mensagem padrão arredondada e determinística.
7.	IA Gemini: Refina a mensagem técnica em uma saudação calorosa (se configurado).
8.	Enviar Resposta: Entrega a mensagem final ao usuário via Telegram, tratando possíveis tags incompatíveis.

🚀 Como importar no n8n

1.	Acesse o painel do seu n8n.
2.	Vá em Workflows -> Import from file.
3.	Selecione o arquivo workflow-telegram-chatbot.json deste repositório.
4.	Clique em Save.

🔐 Configuração das Credenciais

📡 Telegram Bot (via BotFather)

Para criar seu bot e obter o token:
1.	No Telegram, converse com o @BotFather.
2.	Envie o comando /newbot e siga as instruções para definir nome e username.
3.	Copie o API Token fornecido.
4.	No n8n, vá em Credentials -> Add Credential -> Telegram API.
5.	Preencha o campo Access Token e salve. Vincule esta credencial aos nós de Trigger e Envio.

🌡️ OpenWeather API

1.	Crie uma conta em OpenWeatherMap.
2.	Gere uma API Key no painel da sua conta (My API Keys).
3.	No n8n, abra o nó "Configurações Iniciais" e substitua o valor SUA_API_AQUI pela sua chave real.

🧠 Google Gemini

1.	Obtenha sua chave de API no Google AI Studio.
2.	No n8n, crie uma credencial do tipo Google Gemini(PaLM) API.
3.	Insira sua chave e associe a credencial ao nó "Google Gemini Chat Model".

⚙️ Variáveis Esperadas
       
• OPENWEATHER_API_KEY - Chave de acesso à API OpenWeather
• TELEGRAM_BOT_TOKEN - Token de autenticação do Bot Telegram

🌐 Publicar o workflow (Obrigatório)

Para que o bot funcione em tempo real (webhook):
1.	Abra o workflow no n8n.
2.	No canto superior direito, ative a chave Active (ou clique em Publish).
3.	Certifique-se de que o workflow aparece com o status "Active" na sua lista.

🎮 Como usar o chatbot

Inicie uma conversa com seu bot no Telegram e envie o nome da cidade:
•	Formato recomendado: Cidade, UF ou apenas Cidade.
•	Exemplos: Londrina, PR, São Paulo.

Exemplos de Resposta:
•	Sucesso: "Bom dia! Em Londrina, o tempo está ensolarado e a temperatura registra 26°C. Um dia agradável! 🌤️"
•	Erro: "❌ Cidade não encontrada ou fora do Brasil. Use o formato Cidade, UF (ex.: São Paulo, SP)."

✅ Observações Finais
•	Segurança: O arquivo JSON exportado não contém chaves de API reais por segurança.
•	Desenvolvido como critério de avaliação para a Pós-Graduação - 2026.



