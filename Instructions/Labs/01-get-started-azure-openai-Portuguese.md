# Laboratório 01: Iniciar com o Serviço Azure OpenAI

### Duração Estimada: 40 minutos

## Cenário do Laboratório
O Serviço Azure OpenAI traz os modelos de IA generativa desenvolvidos pela OpenAI para a plataforma Azure, permitindo que você desenvolva soluções de IA poderosas que se beneficiam da segurança, escalabilidade e integração dos serviços fornecidos pela plataforma de nuvem Azure. Neste exercício, você aprenderá como começar a usar o Azure OpenAI provisionando o serviço como um recurso do Azure e usando o Azure OpenAI Studio para implantar e explorar modelos OpenAI.

## Objetivos do Laboratório
Neste laboratório, você completará as seguintes tarefas:

- Tarefa 1: Provisionar um recurso Azure OpenAI
- Tarefa 2: Implantar um modelo
- Tarefa 3: Explorar um modelo no playground de Completações
- Tarefa 4: Usar o playground de Chat
- Tarefa 5: Explorar prompts e parâmetros
- Tarefa 6: Explorar a geração de código

### Tarefa 1: Provisionar um recurso Azure OpenAI

Antes de usar os modelos do Azure OpenAI, você deve provisionar um recurso Azure OpenAI na sua assinatura do Azure.

1. No **portal do Azure**, pesquise por **OpenAI** e selecione **Azure OpenAI**.

   ![](../media/openai8.png)

2. Na tela **Serviços de IA do Azure | Azure OpenAI**, clique em **+ Criar**.

   ![](../media/openai_create1.png)

3. Crie um recurso **Azure OpenAI** com as seguintes configurações:
   
    - **Assinatura**: Padrão - Assinatura pré-atribuída.
    - **Grupo de recursos**: openai-<inject key="DeploymentID" enableCopy="false"></inject>
    - **Região**: Selecione <inject key="Region" enableCopy="false" />
    - **Nome**: OpenAI-Lab01-<inject key="DeploymentID" enableCopy="false"></inject>
    - **Camada de preço**: Standard S0
  
   ![](../media/openai-lab01_01.png "Criar recurso Azure OpenAI")

4. Clique em **Avançar** três vezes e clique em **Criar**.

5. Aguarde a conclusão da implantação. Depois, vá para o recurso Azure OpenAI implantado no portal do Azure.

#### Validação

> **Parabéns** por completar a tarefa! Agora é hora de validá-la. Aqui estão os passos:
> - Clique no botão Validar para a tarefa correspondente. Se você receber uma mensagem de sucesso, pode prosseguir para a próxima tarefa. 
> - Caso contrário, leia atentamente a mensagem de erro e tente novamente seguindo as instruções do guia do laboratório.
> - Se precisar de assistência, entre em contato conosco pelo labs-support@spektrasystems.com. Estamos disponíveis 24/7 para ajudar você.

   <validation step="4b6b5a36-2650-4f80-a408-879c57cf61a2" />

### Tarefa 2: Implantar um modelo

O Azure OpenAI fornece um portal baseado na web chamado **Azure OpenAI Studio**, que você pode usar para implantar, gerenciar e explorar modelos. Você começará sua exploração do Azure OpenAI usando o Azure OpenAI Studio para implantar um modelo.

1. No **portal do Azure**, pesquise por **OpenAI** e selecione **Azure OpenAI**.

   ![](../media/openai8.png)

2. Na tela **Serviços de IA do Azure | Azure OpenAI**, selecione **OpenAI-Lab01-<inject key="DeploymentID" enableCopy="false"></inject>**

   ![](../media/OpenAI_select.png)

3. No painel de recursos do Azure OpenAI, clique em **Ir para Azure OpenAI Studio** para navegar até o **Azure AI Studio**.

   ![](../media/openai_studio.png)

4. Após navegar para o Azure AI Studio, clique em **Explore a nova experiência** na parte superior.

   ![](../media/explore_new-exp.jpg)

5. Clique em **Implantações (1)** no painel de navegação à esquerda, clique em **+ Implantar modelo**, selecione **Implantar Modelo Base (2)**.  

   ![](../media/deploy-2.jpg)

6. Na janela **Selecionar um modelo**, selecione **gpt-35-turbo (1)** e clique em **Confirmar (2)**.

   ![](../media/mew5.png)

7. Na interface de **Implantar modelo**, insira os seguintes detalhes:
    
    - **Nome da implantação**: my-gpt-model (1) 
    - **Versão do modelo**: 0613 (2)
    - **Tipo de implantação**: Padrão (3)
    - **Limite de Taxa de Tokens por Minuto (milhares)**: 10K (4)
    - **Habilitar cota dinâmica**: Habilitado (5)
    - Clique em **Implantar** (6)
  
      ![](../media/new3.png)

8. Isso implantará um modelo que você explorará nas próximas etapas.

   > **Nota**: Você pode ignorar qualquer erro relacionado à atribuição de papéis para visualizar os limites de cota.

   > **Nota**: O Azure OpenAI inclui vários modelos, cada um otimizado para um equilíbrio diferente entre capacidades e desempenho. Neste exercício, você usará o modelo **GPT-35-Turbo**, que é um bom modelo geral para resumir e gerar linguagem natural e código. Para mais informações sobre os modelos disponíveis no Azure OpenAI, consulte [Modelos](https://learn.microsoft.com/azure/cognitive-services/openai/concepts/models) na documentação do Azure OpenAI.

#### Validação

<validation step="d9a504d6-e0be-4fa9-a4ed-6ead18a10e03" />

> **Parabéns** por completar a tarefa! Agora é hora de validá-la. Aqui estão os passos:
> - Clique no botão Validar para a tarefa correspondente. Se você receber uma mensagem de sucesso, pode prosseguir para a próxima tarefa. 
> - Caso contrário, leia atentamente a mensagem de erro e tente novamente seguindo as instruções do guia do laboratório.
> - Se precisar de assistência, entre em contato conosco pelo labs-support@spektrasystems.com. Estamos disponíveis 24/7 para ajudar você.

### Tarefa 3: Explorar um modelo no playground de Completações

Os *Playgrounds* são interfaces úteis no Azure OpenAI Studio que você pode usar para experimentar seus modelos implantados sem precisar desenvolver seu próprio aplicativo cliente.

1. No Azure OpenAI Studio, no painel esquerdo, em **Playground**, selecione **Completações**.

2. Na página **Completações**, certifique-se de que sua implantação **my-gpt-model** esteja selecionada e, na lista **Exemplos**, selecione **Gerar um questionário**.

   O texto resumido consiste em um *prompt* que fornece algum texto para dizer ao modelo que tipo de resposta é necessária e inclui algumas informações contextuais.

3. Na parte inferior da página, observe o número de *tokens* detectados no texto. Tokens são as unidades básicas de um prompt - essencialmente palavras ou partes de palavras no texto.

4. Use o botão **Gerar** para enviar o prompt ao modelo e obter uma resposta.

   A resposta consiste em um questionário baseado no exemplo no prompt.

   >**Nota**: Você pode usar o botão **Regenerar** para reenviar o prompt (novas alterações foram feitas) e observe que a resposta pode variar da original. Um modelo de IA generativa pode produzir uma nova linguagem cada vez que é chamado.

5. Use o botão **Ver Código** para visualizar o código que um aplicativo cliente usaria para enviar o prompt. Você pode selecionar sua linguagem de programação preferida. O prompt contém o texto que você enviou ao modelo. A solicitação é enviada à API *Completações* para o seu serviço Azure OpenAI.

### Tarefa 4: Usar o playground de Chat

O *Playground de Chat* fornece uma interface de chatbot para modelos GPT 3.5 e superiores. Ele usa a API *ChatCompletações* em vez da API *Completações* mais antiga.

1. Na seção **Playground**, selecione a página **Chat** e certifique-se de que o modelo **my-gpt-model** esteja selecionado no painel de configuração.

2. Na seção **Configuração**, na caixa **Mensagem do sistema**, substitua o texto atual pela seguinte declaração: `O sistema é um professor de IA que ajuda as pessoas a aprenderem sobre IA`.

3. Abaixo da caixa **Mensagem do sistema**, clique em **+ Adicionar** e insira a seguinte mensagem e resposta nas caixas designadas:

    - **Usuário**: `Quais são os diferentes tipos de inteligência artificial?`
    
    - **Assistente**: `Existem três principais tipos de inteligência artificial: IA Estreita ou Fraca (como assistentes virtuais como Siri ou Alexa, software de reconhecimento de imagem e filtros de spam), IA Geral ou Forte (IA projetada para ser tão inteligente quanto um ser humano. Esse tipo de IA não existe atualmente e é puramente teórico), e Superinteligência Artificial (IA que é mais inteligente do que qualquer ser humano e pode realizar tarefas que estão além da compreensão humana. Esse tipo de IA também é puramente teórico e ainda não foi desenvolvido).`

4. Clique em **Enviar** para iniciar a conversa.

5. Continue a conversa adicionando e respondendo às mensagens do usuário no painel de configuração.

6. Experimente com a personalização das respostas do assistente ajustando as mensagens do sistema ou alterando as mensagens do usuário e do assistente.

### Tarefa 5: Explorar prompts e parâmetros

Os *prompts* são as entradas fornecidas ao modelo, definindo o contexto ou a tarefa que a IA deve realizar. Parâmetros configuram o modelo para otimizar a saída desejada.

1. No playground de Chat, ajuste o prompt fornecido na caixa **Mensagem do Sistema** para `Você é um guia turístico em uma cidade antiga, especializado em história medieval`.

2. Digite a seguinte mensagem de usuário na caixa de mensagem e envie-a:

   `Quais são os marcos mais famosos da cidade e sua importância histórica?`

3. Observe a resposta do assistente, que agora deve se alinhar com o novo contexto.

### Tarefa 6: Explorar a geração de código

1. No **Playground**, selecione **Completações** e, na lista **Exemplos**, selecione **Gerar código Python**.

2. No painel de entrada, o prompt fornecerá um texto para gerar código Python.

3. Clique em **Gerar** para produzir o código.

4. Use o botão **Ver Código** para visualizar o código que um aplicativo cliente usaria para enviar o prompt. Você pode selecionar sua linguagem de programação preferida.

### Resumo

Neste laboratório, você:

- Provisionou um recurso Azure OpenAI
- Implantou um modelo no Azure OpenAI Studio
- Explorou os playgrounds de Completações e Chat
- Ajustou prompts e parâmetros para personalizar a saída do modelo
- Experimentou a geração de código

Agora você tem uma compreensão básica de como usar o Azure OpenAI Studio para experimentar os modelos OpenAI e começar a integrá-los em suas próprias soluções.

