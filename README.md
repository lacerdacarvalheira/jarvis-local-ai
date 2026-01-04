J.A.R.V.I.S V53 - Python AI Assistant
O J.A.R.V.I.S V53 é um assistente virtual modular desenvolvido em Python que combina o poder de processamento local de LLMs (através do Ollama) com automação de desktop e interface gráfica CustomTkinter. O projeto foi estruturado para ser expansível, seguro e capaz de interagir com o sistema operacional de forma inteligente. 
+4

🚀 Funcionalidades Principais

Processamento de Linguagem Natural: Integração com Llama 3.1 para interpretação de comandos e geração de conteúdo. 
+2


Visão Computacional: Capacidade de analisar e descrever a tela do usuário utilizando o modelo Llama 3.2-Vision. 
+3


Controle de Mídia Inteligente: Integração com o YouTube Music que permite buscar, tocar e pular músicas, mantendo o foco na janela de trabalho do usuário. 
+3


Automação de Arquivos e Pastas: Criação dinâmica de diretórios e arquivos .txt com conteúdo gerado automaticamente. 
+2


Integração com WhatsApp: Envio de mensagens instantâneas via PyWhatKit. 
+2


Monitoramento de Hardware: Exibição em tempo real do uso de CPU, RAM e temperatura de GPU na interface. 
+2


Abertura de Aplicativos e Jogos: Suporte nativo para abrir softwares do Windows e integração com a Steam. 
+4


Comandos de Voz: Sistema de reconhecimento de fala integrado com atalho global (Push-to-Talk) e resposta por voz (TTS). 
+1

🛠️ Tecnologias Utilizadas

Interface: CustomTkinter para uma UI moderna e responsiva. 
+3


LLM: Ollama (Llama 3.1 & 3.2-Vision). 
+2


Automação: PyAutoGUI, PyGetWindow e Subprocess. 
+4


Hardware: Psutil e GPUtil. 
+3


Banco de Dados: SQLite3 para persistência de alarmes e configurações. 
+3

📋 Pré-requisitos
Ter o Ollama instalado e os modelos baixados (llama3.1 e llama3.2-vision). 
+2

Instalar as dependências do Python:

Bash

pip install customtkinter ollama ccxt psutil GPUtil pyttsx3 SpeechRecognition
