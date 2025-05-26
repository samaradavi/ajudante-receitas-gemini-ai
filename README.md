# Ajudante de Receitas com Gemini AI 🍳

Este é um script Python para Google Colab que atua como um "Ajudante de Receitas". Ele utiliza a API do Google Generative AI (especificamente o modelo Gemini) para sugerir receitas simples e rápidas com base nos ingredientes fornecidos pelo usuário. O assistente adota a persona de um chef criativo que visa evitar o desperdício de alimentos.

## Funcionalidades

*   **Sugestão de Receitas:** Recebe uma lista de ingredientes e sugere 2-3 receitas.
*   **Criatividade:** Gera nomes divertidos para as receitas.
*   **Simplicidade:** Fornece um passo a passo simples para cada receita.
*   **Foco nos Ingredientes:** Utiliza APENAS os ingredientes fornecidos.
*   **Fallback Inteligente:** Se não for possível criar receitas, informa o usuário de forma amigável.
*   **Integração com Google Colab:** Usa `userdata` para carregar a chave da API de forma segura através dos "Secrets" do Colab.
*   **Modelo Utilizado:** `gemini-1.5-flash-latest`.

## Pré-requisitos

1.  **Conta Google:** Necessária para usar o Google Colab.
2.  **Chave da API do Google Generative AI:**
    *   Você pode obter uma chave de API no [Google AI Studio](https://aistudio.google.com/app/apikey).
    *   Certifique-se de que a API "Generative Language API" está habilitada para o seu projeto no Google Cloud Console, se aplicável (geralmente o AI Studio lida com isso para chaves básicas).

## Configuração

1.  **Abra o Notebook no Google Colab.**
2.  **Adicione sua Chave da API aos Secrets do Colab:**
    *   No painel à esquerda do Colab, clique no ícone de chave (🔑) chamado "Secrets".
    *   Clique em "ADD A NEW SECRET".
    *   **Name:** `GOOGLE_API_KEY`
    *   **Value:** Cole a sua chave da API do Google Generative AI.
    *   Certifique-se de que a opção "Notebook access" está marcada.

## Como Executar

1.  **Instalar a Biblioteca (Célula 1):**
    ```python
    !pip install google-generativeai
    ```
    Execute esta célula para instalar a biblioteca necessária.

2.  **Configurar a API Key e Inicializar (Célula 2):**
    ```python
    import google.generativeai as genai
    from google.colab import userdata # Para pegar nossa chave do cofrinho do Colab!

    # ... (resto do código da célula)
    ```
    Execute esta célula. Ela tentará carregar a `GOOGLE_API_KEY` dos Secrets do Colab e configurar o cliente `genai`.
    *   **Saída Esperada (Sucesso):** `🔑 Chave mágica do Google AI carregada com sucesso do cofrinho do Colab!`
    *   **Saída Esperada (Falha):** Uma mensagem de erro indicando que a chave não foi encontrada ou houve outro problema. Verifique a seção "Configuração" se isso ocorrer.

3.  **Inserir Ingredientes (Célula 3):**
    ```python
    ingredientes_str = input("Oi! 👋 Me diga quais ingredientes você tem na geladeira (separe com vírgula, por exemplo: tomate, queijo, pão): ")
    # ... (resto do código da célula)
    ```
    Execute esta célula. Você será solicitado a inserir os ingredientes que possui, separados por vírgula.
    *   **Exemplo de Input:** `tomate, queijo mussarela, manjericão fresco, pão de forma`

4.  **Gerar e Exibir Receitas (Célula 4):**
    ```python
    model = genai.GenerativeModel('gemini-1.5-flash-latest')
    print("\n🍳 Hmmm, estou pensando em algumas receitas deliciosas para você...")
    # ... (resto do código da célula)
    ```
    Execute esta célula. Ela enviará os ingredientes e o prompt para o modelo Gemini. Após um momento, as sugestões de receitas serão impressas.
    *   **Saída Esperada:** Uma ou mais sugestões de receitas formatadas conforme o prompt, ou a mensagem "Puxa, com esses ingredientes não consigo pensar em nenhuma receita simples agora. Que tal adicionar mais alguma coisa?".

## Exemplo de Saída (Ilustrativo)

Se você inserir `tomate, queijo, pão`:

✨ Aqui estão algumas ideias do Chef Mágico para você! ✨

Olá, amigo(a) da cozinha! Com tomate, queijo e pão, podemos fazer mágicas deliciosas e rápidas! 🧙‍♂️✨

Aqui vão algumas ideias:

1. Torrada Caprese Expressa 🍅🧀🌿

Ingredientes Usados: tomate, queijo, pão.

Como Fazer:

Torre as fatias de pão até ficarem douradinhas.

Corte o tomate em rodelas finas e o queijo em fatias.

Monte sobre o pão torrado: uma fatia de queijo e uma rodela de tomate.

(Opcional: Se tiver um fiozinho de azeite e uma folhinha de manjericão, fica divino!) Leve ao forno/airfryer rapidinho só para o queijo derreter um pouco.

2. Sanduíche Quente Clássico Turbinado 🥪🔥

Ingredientes Usados: pão, queijo, tomate.

Como Fazer:

Monte um sanduíche com fatias de pão, queijo e rodelas de tomate no meio.

Passe um pouquinho de manteiga (se tiver!) por fora do pão.

Leve à frigideira em fogo baixo, dourando dos dois lados até o queijo derreter, ou use sua sanduicheira!

Espero que goste! 😊

Bom apetite! E lembre-se: cozinhar é uma aventura! 🎉

## Solução de Problemas

*   **Erro `Notebook does not have access to secret GOOGLE_API_KEY`:**
    *   Verifique se você adicionou a `GOOGLE_API_KEY` corretamente nos "Secrets" do Colab, conforme a seção "Configuração".
    *   Certifique-se de que o nome do secret é exatamente `GOOGLE_API_KEY` (maiúsculas e sublinhado).
    *   Verifique se a opção "Notebook access" está marcada para o secret.
*   **Nenhuma receita sugerida:** Se o modelo responder com "Puxa, com esses ingredientes não consigo pensar em nenhuma receita simples agora...", tente adicionar mais ingredientes ou ingredientes mais versáteis.
*   **Outros erros da API:** Podem ocorrer devido a problemas temporários com a API do Google, limites de taxa ou configuração incorreta da chave. Tente novamente mais tarde ou verifique o status da API.

---

Aproveite suas criações culinárias!
