# 🚀 Projeto Assistente de Voz com IA (Gemini, Whisper, Edge-TTS)

Este projeto demonstra a criação de um assistente de voz interativo utilizando tecnologias de Inteligência Artificial para reconhecimento de fala, geração de texto e síntese de voz. O objetivo é permitir que os usuários interajam com o assistente por meio de comandos de voz, recebendo respostas em áudio.

## ✨ Funcionalidades

*   **Gravação de Áudio Dinâmica:** Grava o áudio do usuário diretamente no navegador (via JavaScript no Google Colab) e interrompe automaticamente a gravação ao detectar silêncio.
*   **Reconhecimento de Fala (ASR):** Utiliza o modelo Whisper da OpenAI para transcrever o áudio gravado em texto.
*   **Geração de Texto Inteligente:** Integração com a API do Google Gemini para processar a transcrição e gerar respostas textuais coerentes e relevantes.
*   **Síntese de Voz (TTS):** Converte a resposta textual do Gemini de volta para áudio, utilizando a biblioteca `edge-tts` para uma voz natural e gratuita.

## 🛠️ Como Funciona

1.  **Captura de Voz:** Um script JavaScript embarcado no Colab captura o áudio do microfone do usuário.
2.  **Armazenamento:** O áudio é codificado em Base64 e enviado para o backend Python, onde é decodificado e salvo como um arquivo `.mp3`.
3.  **Transcriçã:** O arquivo `.mp3` é processado pelo modelo Whisper, que o converte em texto.
4.  **Processamento com IA:** O texto é enviado à API do Google Gemini, que gera uma resposta inteligente.
5.  **Conversão para Voz:** A resposta do Gemini é sintetizada de volta para áudio (MP3) usando `edge-tts`.
6.  **Reprodução:** O áudio da resposta é reproduzido diretamente no ambiente do Google Colab.

## ⚙️ Pré-requisitos

Para executar este notebook, você precisará:

*   Uma conta Google e acesso ao Google Colab.
*   Um microfone funcional no seu dispositivo.
*   Uma **chave de API para o Google Gemini**. Você pode obtê-la gratuitamente no [Google AI Studio](https://makersuite.google.com/key).

## 🚀 Configuração e Instalação

1.  **Clone o Repositório (se estiver no GitHub):**
    ```bash
    git clone https://github.com/MarceloJSSantos/bootcamp-bradesco-genai-dados-desadio-assistente-voz-whisper-gemini.git
    cd bootcamp-bradesco-genai-dados-desadio-assistente-voz-whisper-gemini
    ```
2.  **Abra no Google Colab:** Faça upload do arquivo `.ipynb` para o Google Colab ou abra-o diretamente se já estiver no GitHub.
3.  **Instale as Dependências:** As células do notebook já incluem comandos para instalar as bibliotecas necessárias automaticamente (`whisper`, `google-generativeai`, `edge-tts`). Execute-as na ordem.
4.  **Configure sua Chave Gemini:**
    *   No Colab, clique no ícone de chave (🔑) no painel esquerdo.
    *   Adicione um novo segredo com o nome `GOOGLE_API_KEY` (ou `minha_chave` como no notebook atual) e cole sua chave de API do Gemini.
    *   Altere a variável `minha_chave` na célula `79_5p-SDGS3S` para carregar a chave dos segredos do Colab ou para o nome que você definiu.

    ```python
    # Exemplo de como usar o Secrets do Colab
    from google.colab import userdata
    minha_chave = userdata.get('GOOGLE_API_KEY') # Se você nomeou o segredo como GOOGLE_API_KEY
    genai.configure(api_key=minha_chave)
    ```

## 🎙️ Como Usar

Basta executar as células do notebook em sequência. O fluxo é:

1.  **Definição de Idioma** (Célula 1)
2.  **Definição do Script JavaScript de Gravação** (Célula 2)
3.  **Início da Gravação:** Ao executar a célula 3, o navegador solicitará permissão para usar o microfone. Fale sua pergunta ou comando após o prompt e pare de falar para que a gravação seja finalizada por silêncio.
4.  **Instalação e Carregamento do Whisper** (Células 4 e 5): Transcreve seu áudio.
5.  **Instalação e Configuração do Gemini** (Células 6 e 7): Gera a resposta textual.
6.  **Instalação e Síntese de Voz (edge-tts)** (Células 8 e 9): Converte a resposta em áudio e a reproduz.

## 📝 Notas Importantes

*   **Modelo Gemini:** O notebook tenta usar `gemini-2.5-flash`. Se houver erros ou indisponibilidade em sua região, a célula exibirá outros modelos disponíveis que você pode tentar usar (por exemplo, `gemini-1.5-flash`).
*   **Sensibilidade do Microfone:** A detecção de silêncio no script JavaScript (`SCRIPT_JS_RECORD`) pode ser ajustada alterando o valor de `THRESHOLD` se a gravação não estiver parando corretamente ou estiver capturando muito ruído ambiente.

## 💡 Possíveis Melhorias Futuras

*   **Interface Gráfica (GUI):** Implementar uma interface web mais amigável (ex: Streamlit, Gradio) para uma experiência de usuário mais rica fora do Colab.
*   **Streaming de Áudio:** Gravação e transcrição em tempo real para reduzir a latência na interação.
*   **Gerenciamento de Contexto:** Adicionar capacidade de manter o contexto da conversa com o Gemini para diálogos mais fluidos.
*   **Suporte a Múltiplos Idiomas:** Expandir o suporte para reconhecimento e síntese de voz em outros idiomas.
*   **Detecção de Intenção:** Integrar um modelo de NLU para entender a intenção do usuário e executar ações específicas.

---
