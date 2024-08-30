# Laboratório 02: Use SDKs do Azure OpenAI em seu aplicativo

### Duração Estimada: 40 minutos

## Cenário do laboratório
Com o Serviço Azure OpenAI, os desenvolvedores podem criar chatbots, modelos de linguagem e outras aplicações que se destacam na compreensão da linguagem humana natural. O Azure OpenAI fornece acesso a modelos de IA pré-treinados, bem como um conjunto de APIs e ferramentas para personalizar e ajustar esses modelos para atender aos requisitos específicos da sua aplicação. Neste exercício, você aprenderá como implantar um modelo no Azure OpenAI e usá-lo em seu próprio aplicativo.

No cenário deste exercício, você desempenhará o papel de um desenvolvedor de software que foi encarregado de implementar um aplicativo que pode usar IA generativa para ajudar a fornecer recomendações de caminhadas. As técnicas usadas no exercício podem ser aplicadas a qualquer aplicativo que queira usar as APIs do Azure OpenAI.

## Objetivos do laboratório
Neste laboratório, você completará as seguintes tarefas:

- Tarefa 1: Provisionar um recurso Azure OpenAI
- Tarefa 2: Implantar um modelo
- Tarefa 3: Configurar um aplicativo no Cloud Shell
- Tarefa 4: Configurar seu aplicativo
- Tarefa 5: Executar seu aplicativo

## Tarefa 1: Provisionar um recurso Azure OpenAI

Antes de poder usar os modelos Azure OpenAI, você deve provisionar um recurso Azure OpenAI em sua assinatura do Azure.

1. No **portal do Azure**, pesquise por **OpenAI** e selecione **Azure OpenAI**.

   ![](../media/openai8.png)

2. Na lâmina **Azure AI Services | Azure OpenAI**, clique em **+ Criar**.

   ![](../media/openai_create1.png)

3. Crie um recurso **Azure OpenAI** com as seguintes configurações 

    - **Assinatura**: Default - Assinatura pré-atribuída (1).
    - **Grupo de recursos**: openai-<inject key="DeploymentID" enableCopy="false"></inject> (2)
    - **Região**: Selecione <inject key="Region" enableCopy="false" /> (3)
    - **Nome**: OpenAI-Lab02-<inject key="DeploymentID" enableCopy="false"></inject> (4)
    - **Nível de preços**: Standard S0 (5)
    - Clique em **Próximo** (6)
  
        ![](../media/azopenai123.png "Criar recurso Azure OpenAI")

4. Clique em **Próximo** duas vezes e subsequentemente clique em **Criar** 

5. Aguarde a conclusão da implantação. Em seguida, vá para o recurso Azure OpenAI implantado no portal do Azure.

6. Para capturar os valores de Chaves e Endpoints, na lâmina **openai-<inject key="DeploymentID" enableCopy="false"></inject>**:
      - Selecione **Chaves e Endpoint (1)** sob **Gerenciamento de Recursos**.
      - Clique em **Mostrar Chaves (2)**.
      - Copie a **Chave 1 (3)** e certifique-se de colá-la em um editor de texto como o Bloco de Notas para referência futura.
      - Finalmente, copie a URL da API do **Endpoint (4)** clicando em copiar para a área de transferência. Cole-a em um editor de texto como o Bloco de Notas para uso posterior.

        ![](../media/openai-endpoint-new.png "Chaves e Endpoints")

#### Validação

> **Parabéns** por completar a tarefa! Agora, é hora de validá-la. Aqui estão os passos:
> - Clique no botão Validar para a tarefa correspondente. Se você receber uma mensagem de sucesso, pode prosseguir para a próxima tarefa. 
> - Caso contrário, leia atentamente a mensagem de erro e tente novamente o passo, seguindo as instruções no guia do laboratório.
> - Se precisar de alguma assistência, por favor, entre em contato conosco em labs-support@spektrasystems.com. Estamos disponíveis 24/7 para ajudá-lo.

   <validation step="6b7e8754-7031-45fb-a340-762578ad9685" />

## Tarefa 2: Implantar um modelo

Para usar a API do Azure OpenAI, você deve primeiro implantar um modelo para usar através do **Azure OpenAI Studio**. Uma vez implantado, faremos referência a esse modelo em nosso aplicativo.

1. No **portal do Azure**, pesquise por **OpenAI** e selecione **Azure OpenAI**.

   ![](../media/openai8.png)

2. Na lâmina **Azure AI Services | Azure OpenAI**, selecione **OpenAI-Lab02-<inject key="DeploymentID" enableCopy="false"></inject>**

   ![](../media/OpenAI_select.png)

3. No painel de recursos do Azure OpenAI, clique em **Ir para o Azure OpenAI Studio** e ele navegará para o **Azure AI Studio**.

   ![](../media/openai_studio1.png)

4. Após navegar para o Azure AI Studio, clique no pop-up **Explore a nova experiência** no topo.

   ![](../media/explore_new-exp.jpg)

5. Clique em **Implantações (1)** no painel de navegação à esquerda, clique em **+ Implantar modelo** , selecione **Implantar modelo base (2)**.  

   ![](../media/deploy-2.jpg)

6. Na janela **Selecionar um modelo**, selecione **gpt-35-turbo-16k (1)** e clique em **Confirmar (2)**.

   ![](../media/new4.png)

7. Na interface pop-up **Implantar modelo**, insira os seguintes detalhes:
    
    - **Nome da implantação**: text-turbo (1) 
    - **Versão do modelo**: 0613(Padrão) (2)
    - **Tipo de implantação**: Padrão (3)
    - **Limite de Taxa de Tokens por Minuto (milhares)**: 10K (4)
    - **Habilitar cota dinâmica**: Habilitado (5)
    - Clique em **Implantar** (6)
  
      ![](../media/new2.png)

8. Isso implantará um modelo com o qual você brincará à medida que avançar.

   > **Nota**: Você pode ignorar a notificação "Falha ao buscar informações de cota de implantações".
   
   > **Nota**: Cada modelo Azure OpenAI é otimizado para um equilíbrio diferente de capacidades e desempenho. Usaremos a série de modelos **3.5 Turbo** na família de modelos **GPT-3** neste exercício, que é altamente capaz de compreensão de linguagem. Este exercício usa apenas um único modelo, no entanto, a implantação e o uso de outros modelos que você implantar funcionarão da mesma maneira.

#### Validação

> **Parabéns** por completar a tarefa! Agora, é hora de validá-la. Aqui estão os passos:
> - Clique no botão Validar para a tarefa correspondente. Se você receber uma mensagem de sucesso, pode prosseguir para a próxima tarefa. 
> - Caso contrário, leia atentamente a mensagem de erro e tente novamente o passo, seguindo as instruções no guia do laboratório.
> - Se precisar de alguma assistência, por favor, entre em contato conosco em labs-support@spektrasystems.com. Estamos disponíveis 24/7 para ajudá-lo.

   <validation step="4799e712-2f03-4a88-9456-fca39aea25d0" />

## Tarefa 3: Configurar um aplicativo no Cloud Shell

Para mostrar como integrar com um modelo Azure OpenAI, usaremos um aplicativo de linha de comando curto que é executado no Cloud Shell no Azure. Abra uma nova guia do navegador para trabalhar com o Cloud Shell.

1. No [portal do Azure](https://portal.azure.com?azure-portal=true), selecione o botão **[>_]** (*Cloud Shell*) na parte superior da página à direita da caixa de pesquisa. Um painel do Cloud Shell será aberto na parte inferior do portal.

    ![Captura de tela do início do Cloud Shell clicando no ícone à direita da caixa de pesquisa superior.](../media/cloudshell-launch-portal.png#lightbox)

2. Na primeira vez que você abrir o Cloud Shell, você pode ser solicitado a escolher o tipo de shell que deseja usar (*Bash* ou *PowerShell*). Selecione **Bash**. Se você não vir esta opção, pule o passo.

3. Dentro do painel Começando, selecione **Montar conta de armazenamento**, selecione sua **Assinatura de conta de armazenamento** no menu suspenso e clique em **Aplicar**.

   ![](../media/cloudshell-getting-started.png)

4. Dentro do painel **Montar conta de armazenamento**, selecione **Eu quero criar uma conta de armazenamento** e clique em **Próximo**.

   ![](../media/cloudshell-mount-strg-account.png)

5. Dentro do painel **Configurações avançadas**, insira os seguintes detalhes:

    - **Assinatura**: Default- Escolha a única assinatura existente atribuída para este laboratório (1).
    - **Região**: <inject key="Region" enableCopy="false" /> (2)
    - **Grupo de recursos**: Selecione **Usar existente** (3)
      - openai-<inject key="DeploymentID" enableCopy="false"></inject>
    - **Conta de armazenamento**: Selecione **Criar nova** (4)
      - storage<inject key="DeploymentID" enableCopy="false"></inject>
    - **Compartilhamento de arquivo**: Crie um novo compartilhamento de arquivo chamado **none** (5)
    - Clique em **Criar** (6)

        ![](../media/cloudshell-advanced-settings.png "Criar configurações avançadas de armazenamento")

6. Note que você pode redimensionar o cloud shell arrastando a barra separadora na parte superior da página, ou usando os ícones **&#8212;**, **&#9723;**, e **X** no canto superior direito da página para minimizar, maximizar e fechar o painel. Para mais informações sobre como usar o Azure Cloud Shell, consulte a [documentação do Azure Cloud Shell](https://docs.microsoft.com/azure/cloud-shell/overview). 

7. Uma vez que o terminal inicie, insira o seguinte comando para baixar o aplicativo de amostra e salvá-lo em uma pasta chamada `azure-openai`.

    ```bash
   rm -r azure-openai -f
   git clone https://github.com/MicrosoftLearning/mslearn-openai azure-openai
    ```
  
8. Os arquivos são baixados para uma pasta chamada **azure-openai**. Navegue até os arquivos do laboratório para este exercício usando o seguinte comando.

    ```bash
   cd azure-openai/Labfiles/02-azure-openai-api
    ```

    Aplicativos para C# e Python foram fornecidos, bem como um arquivo de texto de amostra que você usará para testar a sumarização. Ambos os aplicativos apresentam a mesma funcionalidade.

9. Abra o editor de código integrado e observe o arquivo de texto que você estará resumindo com seu modelo localizado em `text-files/sample-text.txt`. Use o seguinte comando para abrir os arquivos do laboratório no editor de código.

    ```bash
    code .
    ```
    > **NOTA:** Se você for solicitado a **Mudar para o Cloud Shell Clássico** após executar o comando **code .**, clique em **Confirmar** e execute os passos 8 e 9 novamente.

   ![](../media/classic-cloudshell-prompt.png) 
   
#### Validação

<validation step="2e8dadd1-f827-4597-8d99-c814ec85fbab" />

> **Parabéns** por completar a tarefa! Agora, é hora de validá-la. Aqui estão os passos:
> - Clique no botão Validar para a tarefa correspondente. Se você receber uma mensagem de sucesso, pode prosseguir para a próxima tarefa. 
> - Caso contrário, leia atentamente a mensagem de erro e tente novamente o passo, seguindo as instruções no guia do laboratório.
> - Se precisar de alguma assistência, por favor, entre em contato conosco em labs-support@spektrasystems.com. Estamos disponíveis 24/7 para ajudá-lo.


