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

## Tarefa 1: Provisionar um recurso Azure OpenAI

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

## Tarefa 2: Implantar um modelo

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

## Tarefa 3: Explorar um modelo no playground de Completações

Os *Playgrounds* são interfaces úteis no Azure OpenAI Studio que você pode usar para experimentar seus modelos implantados sem precisar desenvolver seu próprio aplicativo cliente.

1. No Azure OpenAI Studio, no painel esquerdo, em **Playground**, selecione **Completações**.

2. Na página **Completações**, certifique-se de que sua implantação **my-gpt-model** esteja selecionada e, na lista **Exemplos**, selecione **Gerar um questionário**.

   O texto resumido consiste em um *prompt* que fornece algum texto para dizer ao modelo que tipo de resposta é necessária e inclui algumas informações contextuais.

3. Na parte inferior da página, observe o número de *tokens* detectados no texto. Tokens são as unidades básicas de um prompt - essencialmente palavras ou partes de palavras no texto.

4. Use o botão **Gerar** para enviar o prompt ao modelo e obter uma resposta.

   A resposta consiste em um questionário baseado no exemplo no prompt.

   >**Nota**: Você pode usar o botão **Regenerar** para reenviar o prompt (novas alterações foram feitas) e observe que a resposta pode variar da original. Um modelo de IA generativa pode produzir uma nova linguagem cada vez que é chamado.

5. Use o botão **Ver Código** para visualizar o código que um aplicativo cliente usaria para enviar o prompt. Você pode selecionar sua linguagem de programação preferida. O prompt contém o texto que você enviou ao modelo. A solicitação é enviada à API *Completações* para o seu serviço Azure OpenAI.

## Tarefa 4: Use o playground de chat

O playground de chat fornece uma interface de chatbot para os modelos GPT 3.5 e superiores. Ele usa a API ChatCompletions em vez da API Completions mais antiga.

1. Na seção Playground, selecione a página de Chat e certifique-se de que o modelo my-gpt-model está selecionado no painel de configuração.

2. Na seção Configuração, na caixa de mensagem do Sistema, substitua o texto atual pela seguinte declaração: O sistema é um professor de IA que ajuda as pessoas a aprender sobre IA.

3. Abaixo da caixa de mensagem do Sistema, clique em + Adicionar e insira a seguinte mensagem e resposta nas caixas designadas:

   Usuário: Quais são os diferentes tipos de inteligência artificial?

   Assistente: Existem três tipos principais de inteligência artificial: IA Estreita ou Fraca (como assistentes virtuais como Siri ou Alexa, software de reconhecimento de imagem e filtros de spam), IA Geral ou Forte (IA projetada para ser tão inteligente quanto um ser humano. Este tipo de IA ainda não existe e é puramente teórica), e Superinteligência Artificial (IA que é mais inteligente do que qualquer ser humano e pode realizar tarefas que estão além da compreensão humana. Este tipo de IA também é puramente teórico e ainda não foi desenvolvido).

   Nota: Exemplos de poucos tiros são usados para fornecer ao modelo exemplos dos tipos de respostas esperadas. O modelo tentará refletir o tom e o estilo dos exemplos em suas próprias respostas.

4. Clique em Aplicar alterações e depois clique em Continuar na aba pop-up Atualizar mensagem do sistema para iniciar uma nova sessão e definir o contexto comportamental do sistema de chat.

5. Na caixa de consulta na parte inferior da página, insira o texto O que é inteligência artificial?

6. Use o botão Enviar para submeter a mensagem e ver a resposta.

   Nota: Você pode receber uma resposta informando que o deploy da API ainda não está pronto. Se isso acontecer, aguarde alguns minutos e tente novamente.

7. Revise a resposta e então envie a seguinte mensagem para continuar a conversa: Como isso está relacionado ao aprendizado de máquina?

8. Revise a resposta, observando que o contexto da interação anterior é retido (para que o modelo entenda que "isso" se refere à inteligência artificial).

9. Use o botão Ver Código para visualizar o código para a interação. O prompt consiste na mensagem do sistema, nos exemplos de mensagens de usuário e assistente, e na sequência de mensagens de usuário e assistente na sessão de chat até agora.

## Tarefa 5: Explore prompts e parâmetros

Você pode usar o prompt e os parâmetros para maximizar a probabilidade de gerar a resposta que você precisa.

1. No painel de Configuração, selecione Parâmetro, defina os seguintes valores de parâmetro:

   - Temperatura: 0
   - Máx resposta (Número máximo de tokens): 500

2. Submeta a seguinte mensagem na sessão de chat:

   Escreva três perguntas de múltipla escolha com base no seguinte texto.

   A maioria das soluções de visão computacional é baseada em modelos de aprendizado de máquina que podem ser aplicados a entradas visuais de câmeras, vídeos ou imagens.*

   - Classificação de imagem envolve treinar um modelo de aprendizado de máquina para classificar imagens com base em seu conteúdo. Por exemplo, em uma solução de monitoramento de tráfego, você pode usar um modelo de classificação de imagem para classificar imagens com base no tipo de veículo que elas contêm, como táxis, ônibus, ciclistas e assim por diante.*

   - Detecção de objetos são modelos de aprendizado de máquina treinados para classificar objetos individuais dentro de uma imagem e identificar sua localização com uma caixa delimitadora. Por exemplo, uma solução de monitoramento de tráfego pode usar detecção de objetos para identificar a localização de diferentes classes de veículos.*

   - Segmentação semântica é uma técnica avançada de aprendizado de máquina na qual pixels individuais na imagem são classificados de acordo com o objeto ao qual pertencem. Por exemplo, uma solução de monitoramento de tráfego pode sobrepor imagens de tráfego com camadas de "máscara" para destacar diferentes veículos usando cores específicas.

3. Revise os resultados, que devem consistir em perguntas de múltipla escolha que um professor poderia usar para testar os alunos sobre os tópicos de visão computacional no prompt. A resposta total deve ser menor do que o comprimento máximo especificado como parâmetro.

   Observe o seguinte sobre o prompt e os parâmetros que você usou:

   - O prompt especifica que a saída desejada deve ser três perguntas de múltipla escolha.
   - Os parâmetros incluem Temperatura, que controla o grau de aleatoriedade na geração da resposta. O valor de 0 usado na sua submissão minimiza a aleatoriedade, resultando em respostas estáveis e previsíveis.

## Tarefa 6: Explore a geração de código

Além de gerar respostas em linguagem natural, você pode usar modelos GPT para gerar código.

1. No painel de Configuração, selecione o template Exemplo Vazio e então clique em Continuar na aba pop-up Atualizar mensagem do sistema para redefinir a mensagem do sistema.

2. Digite a mensagem do sistema: Você é um desenvolvedor Python. e clique em Aplicar alterações e então clique em Continuar na aba pop-up Atualizar mensagem do sistema.

3. Na seção de Chat, selecione Limpar chat e então clique em Limpar na aba Limpar chat para limpar o histórico de chat e iniciar uma nova sessão.

4. Submeta a seguinte mensagem do usuário:

   Escreva uma função Python chamada Multiply que multiplique dois parâmetros numéricos.

5. Revise a resposta, que deve incluir um código Python de exemplo que atenda ao requisito no prompt.

## Resumo

Neste laboratório, você realizou o seguinte:

- Provisionou um recurso Azure OpenAI
- Implantou um modelo Azure OpenAI no Azure OpenAI studio
- Usou o playground de chat para utilizar as funcionalidades de prompts, parâmetros e geração de código

Você completou com sucesso o laboratório.
