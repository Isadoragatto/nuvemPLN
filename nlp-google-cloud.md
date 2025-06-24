# Serviços de NLP na Google Cloud Platform

A Google Cloud Platform ou GCP, é a nuvem do Google. Ela tem vários serviços online que ajudam empresas, desenvolvedores e até estudantes a criarem sites, aplicativos, sistemas e ferramentas de inteligência artificial usando a mesma estrutura que o Google usa no YouTube, Gmail e no próprio buscador.

Com a GCP, não é preciso ter servidores físicos ou se preocupar com espaço ou segurança. Tudo funciona direto na internet, com um bom desempenho, proteção de dados e a possibilidade de crescer conforme o projeto for aumentando.

### Para que serve?

A GCP pode ser usada para muitas coisas, como por exemplo:
- Criar e hospedar sites e aplicativos
- Armazenar e organizar dados
- Analisar informações de forma inteligente
- Usar inteligência artificial para entender textos, imagens, vozes e mais
- Automatizar tarefas usando APIs prontas
- Trabalhar com grandes quantidades de dados de forma rápida

### Por que ela é boa?

- Usa a infraestrutura do próprio Google, que é rápida e segura
- Tem data centers espalhados pelo mundo todo
- Oferece ferramentas modernas, como o BigQuery, Kubernetes e várias APIs de IA
- Funciona com várias linguagens de programação
- Pode ser usada tanto por iniciantes quanto por profissionais

---

A GCP também facilita o uso de **NLP (Processamento de Linguagem Natural)**, que é a tecnologia que entende textos escritos. Com as ferramentas de NLP da Google Cloud, dá pra descobrir se um texto é positivo ou negativo, identificar nomes de pessoas ou empresas, ver o idioma, entender a estrutura das frases, entre outras funções — tudo isso com apenas uma chamada de API.


## Serviços de NLP disponíveis na GCP

### 1. Análise de Sentimento
- **O que faz**: Identifica se o texto tem um tom positivo, negativo ou neutro.
- **Exemplo de uso**: Uma empresa pode usar isso para analisar os comentários dos clientes e saber se eles estão satisfeitos ou não com o serviço.

#### Exemplo de requisição HTTP (Análise de Sentimento):

```http
POST https://language.googleapis.com/v1/documents:analyzeSentiment?key=SUA_API_KEY
Content-Type: application/json

{
  "document": {
    "type": "PLAIN_TEXT",
    "content": "Gostei muito do produto, mas a entrega demorou demais."
  },
  "encodingType": "UTF8"
}
```
### Explicação da requisição:
- `POST:` Envia dados para a API processar.

- `https://language.googleapis.com/v1/documents:analyzeSentiment:` Endpoint específico para análise de sentimento.

- `key=SUA_API_KEY:` Chave de autenticação da API.

- `Content-Type:` application/json: Indica que os dados estão no formato JSON.

**Corpo da requisição:**

- `"type": "PLAIN_TEXT":` Informa que o conteúdo enviado é texto simples.

- `"content":` Texto que será analisado.

- `"encodingType": "UTF8":` Define a codificação de caracteres usada.

**Retorno esperado:**

Um JSON com os campos score (polaridade do sentimento) e magnitude (intensidade emocional).


### 2. Extração de Entidades

- **O que faz:** Identifica e categoriza entidades nomeadas em um texto (pessoas, organizações, localizações, datas, valores monetários, entre outros). A API também retorna a saliência da entidade (relevância no contexto do texto) e um identificador no Google Knowledge Graph, quando aplicável.

- **Exemplo de uso:**  Útil para indexação automatizada de documentos, sistemas de perguntas e respostas, mecanismos de busca interna e criação de grafos de conhecimento com base em conteúdo textual.

#### Exemplo de requisição HTTP (Extração de Entidades):

```http
POST https://language.googleapis.com/v1/documents:analyzeEntities?key=SUA_API_KEY
Content-Type: application/json

{
  "document": {
    "type": "PLAIN_TEXT",
    "content": "Sundar Pichai é o CEO da Alphabet e mora na Califórnia, nos Estados Unidos."
  },
  "encodingType": "UTF8"
}
```

**Explicação da requisição:**

- `POST`: Envia texto para ser analisado.

- `https://language.googleapis.com/v1/documents:analyzeEntities`: Endpoint para identificar entidades nomeadas.

- `key=SUA_API_KEY`: Chave da sua conta no Google Cloud para autenticação.

- `Content-Type`: application/json: Formato do conteúdo enviado.

**Corpo da requisição:**

- `"type": "PLAIN_TEXT"`: Indica que o texto é simples.

- `"content"`: O texto onde as entidades serão buscadas.

- `"encodingType": "UTF8"`: Codificação do texto.

**Retorno esperado:**
- Um JSON com uma lista de entidades detectadas, contendo:

- `name`: Nome da entidade

- `type`: Tipo (PERSON, LOCATION, ORGANIZATION etc.)

- `salience`: Importância da entidade no contexto do texto

- `metadata`: Informações adicionais, como links para o Google Knowledge Graph


### 3. Análise de Sintaxe

- **O que faz**: Fornece uma análise linguística detalhada, incluindo o tipo de cada token (palavra ou pontuação), função gramatical (sujeito, predicado, objeto etc.), lema (forma base da palavra) e dependências sintáticas. Isso permite entender a estrutura e relações gramaticais do texto.
- **Exemplo de uso**: Pode ser integrado a sistemas de correção gramatical, assistentes virtuais, ou modelos que dependem de compreensão sintática para gerar ou responder em linguagem natural.


### 4. Classificação de Conteúdo

- **O que faz**:Classifica automaticamente documentos com mais de 20 palavras em categorias predefinidas com base em um modelo treinado pelo Google. As categorias seguem uma hierarquia temática, como “Computação e Eletrônicos”, “Esportes” ou “Saúde”.
- **Exemplo de uso**: Plataformas de gerenciamento de conteúdo podem aplicar esse serviço para rotular automaticamente artigos, notícias ou postagens, facilitando a organização e recomendação de conteúdos ao usuário.

### 5. Detecção de Idioma

- **O que faz**:   A API identifica automaticamente o idioma do texto enviado. Essa detecção é fundamental para ajustar os modelos linguísticos usados nas análises de sentimento, entidades e sintaxe.
- **Exemplo de uso**:  Ferramentas de atendimento ao cliente multilingues, chatbots ou qualquer aplicação que receba textos em idiomas variados podem usar essa funcionalidade para direcionar o processamento corretamente.

