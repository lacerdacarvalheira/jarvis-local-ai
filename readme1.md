# Jarvis V53 - Local AI Assistant (Production Grade)

> Uma aplicação desktop concorrente orientada a IA, projetada com princípios de engenharia de software resiliente: isolamento de falhas, shutdown coordenado, idempotência, persistência e controle de thread-safety.

## 🏗️ Arquitetura

O sistema opera em uma arquitetura de **Executores Desacoplados**, separando a Interface Gráfica (GUI) das operações pesadas para garantir fluidez total.

### Componentes Principais:
1.  **GUI (Main Thread):** CustomTkinter. Responsável *apenas* por renderizar e capturar eventos.
2.  **Cérebro (Logic Layer):** Roteador de intenções híbrido (Regex/Keyword + Llama 3.1).
3.  **Executores (Worker Pools):**
    * `IO_POOL` (4 Workers): Rede, Disco, WhatsApp, Web Search.
    * `CPU_POOL` (2 Workers): Inferência LLM, Processamento de Dados.
4.  **State Manager (Thread-Safe):** Classe Singleton com `threading.Lock` para gerenciar memória compartilhada e listas de monitoramento.
5.  **Persistência:** SQLite (`jarvis.db`) para recuperação de estado (Alarmes/Configs) pós-reboot.
6.  **Output Layer:** Fila de áudio (`queue.Queue`) com thread dedicada para TTS (Text-to-Speech), prevenindo deadlocks de driver.

## 🛡️ Segurança e Robustez

* **Whitelist Estrita:** A IA só pode executar ações pré-aprovadas (`TIPOS_PERMITIDOS`).
* **Human-in-the-Loop:** Ações críticas (ex: Desligar PC) exigem confirmação via Popup (implementado com `threading.Event` para evitar travamento da UI).
* **Sanitização:** Entradas de sistema de arquivos são limpas contra caracteres ilegais.
* **Graceful Shutdown:** Encerramento coordenado de pools, drivers de áudio e conexões de banco de dados.

## 🚀 Como Rodar

### Pré-requisitos
1.  Python 3.10+
2.  [Ollama](https://ollama.com/) rodando localmente (`ollama serve`).
3.  Modelos baixados: `ollama pull llama3.1` e `ollama pull llama3.2-vision`.
4.  FFmpeg instalado e no PATH do sistema.

### Instalação
```bash
pip install -r requirements.txt
python jarvis_v53.py