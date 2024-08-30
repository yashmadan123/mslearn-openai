# Comece com o OpenAI e Construa Soluções de Linguagem Natural

### Duração Estimada Total: 4 Horas

## Visão Geral

O Azure OpenAI Service traz os modelos de IA generativa desenvolvidos pela OpenAI para a plataforma Azure, permitindo o desenvolvimento de soluções de IA poderosas com a segurança, escalabilidade e integração dos serviços em nuvem do Azure. Neste laboratório, você aprenderá a provisionar o Azure OpenAI como um recurso e usar o Azure OpenAI Studio para implantar e explorar os modelos da OpenAI. Com o Azure OpenAI, os desenvolvedores podem criar aplicações como chatbots e modelos de linguagem que se destacam na compreensão da linguagem humana natural. O serviço oferece acesso a modelos de IA pré-treinados e um conjunto de APIs e ferramentas para personalizar e ajustar esses modelos para atender aos requisitos específicos da aplicação. Neste cenário, você assumirá o papel de um desenvolvedor de software encarregado de implementar um aplicativo para fornecer recomendações de trilhas de caminhada usando IA generativa, demonstrando técnicas aplicáveis a qualquer aplicativo que utilize as APIs do Azure OpenAI.

## Objetivo

Ao final deste laboratório, você será capaz de:

- **Começar com o Azure OpenAI Service**: Este exercício prático visa provisionar um recurso Azure OpenAI e implantar um modelo. Explore as capacidades do modelo no playground de Completions, depois interaja com ele usando o playground de Chat. Ajuste as respostas ajustando prompts e parâmetros, e aproveite a geração de código para automatizar tarefas.
- **Usar os SDKs do Azure OpenAI em seu aplicativo**: Este exercício prático visa provisionar um recurso Azure OpenAI, implantar um modelo, configurar e configurar um aplicativo no Cloud Shell e, em seguida, executar o aplicativo, demonstrando todo o ciclo de vida, desde a criação do recurso até a implantação e execução do aplicativo.

## Pré-requisitos

- Familiaridade com o Azure OpenAI Service, Azure CLI e APIs REST
- Compreensão básica de conceitos de IA e aprendizado de máquina

## Arquitetura

O fluxo de arquitetura para esta tarefa começa com o provisionamento de um recurso Azure OpenAI em sua assinatura do Azure e a implantação de um modelo pré-treinado usando o Azure OpenAI Studio. Em seguida, você explorará as capacidades do modelo no playground de Completions e testará suas habilidades conversacionais no playground de Chat, experimentando diferentes prompts e parâmetros para personalizar as respostas. Você também investigará as capacidades de geração de código do modelo. Na fase de desenvolvimento do aplicativo, você configurará seu ambiente de aplicativo no Azure Cloud Shell, configurará o aplicativo para integrar com o modelo OpenAI implantado e, finalmente, executará o aplicativo para fornecer recomendações de trilhas de caminhada usando IA generativa.

## Diagrama de Arquitetura

![Acesse sua VM e Guia do Laboratório](../media/arch20.png)

## Explicação dos Componentes

1. **Azure OpenAI**: O Azure OpenAI Service fornece acesso via API REST aos poderosos modelos de linguagem da OpenAI e esses modelos se integram aos seus dados, permitindo interações personalizadas e seguras.
2. **Modelos Azure OpenAI**: Oferece modelos de linguagem pré-treinados e personalizáveis para várias aplicações de IA. Esses modelos permitem soluções avançadas baseadas em IA gerando conteúdo adaptado e contextualmente relevante com base em prompts bem elaborados.
3. **Azure CloudShell**: O Azure CloudShell oferece uma experiência de shell integrada e baseada em navegador para gerenciar recursos do Azure. Ele fornece um ambiente pronto para uso com ferramentas pré-instaladas e acesso tanto ao Bash quanto ao PowerShell.

## Começando com o Laboratório

### Acessando seu Ambiente de Laboratório

Uma vez pronto para começar, sua máquina virtual e o guia do laboratório estarão ao seu alcance diretamente no seu navegador da web.

![Acesse sua VM e Guia do Laboratório](../media/labguide-1.png)

### Máquina Virtual & Guia do Laboratório

Sua máquina virtual é seu principal recurso durante o workshop. O guia do laboratório é seu roteiro para o sucesso.

### Explorando Seus Recursos de Laboratório

Para entender melhor seus recursos e credenciais de laboratório, navegue até a guia **Ambiente**.

![Explore os Recursos do Laboratório](../media/env-1.png)

### Utilizando o Recurso de Janela Dividida

Para conveniência, você pode abrir o guia do laboratório em uma janela separada selecionando o botão **Janela Dividida** no canto superior direito.

![Use o Recurso de Janela Dividida](../media/spl.png)

### Gerenciando Sua Máquina Virtual

Sinta-se à vontade para iniciar, parar ou reiniciar sua máquina virtual conforme necessário na guia **Recursos**. Sua experiência está em suas mãos!

![Gerencie sua Máquina Virtual](../media/res.png)

## Extensão da Duração do Laboratório

1. Para estender a duração do laboratório, clique no ícone **Ampulheta** no canto superior direito do ambiente do laboratório.

    ![Gerencie sua Máquina Virtual](../media/gext.png)

    > **Nota:** Você verá o ícone **Ampulheta** quando restarem 10 minutos no laboratório.

2. Clique em **OK** para estender a duração do seu laboratório.

   ![Gerencie sua Máquina Virtual](../media/gext2.png)

3. Se você não tiver estendido a duração antes do final do laboratório, uma janela pop-up aparecerá, dando-lhe a opção de estender. Clique em **OK** para prosseguir.

## Vamos Começar com o Portal do Azure

1. Na sua máquina virtual, clique no ícone do Portal do Azure conforme mostrado abaixo:

   ![Iniciar o Portal do Azure](../media/sc900-image(1).png)

2. Você verá a aba **Entrar no Microsoft Azure**. Aqui, insira suas credenciais:

   - **Email/Usuário:** <inject key="AzureAdUserEmail"></inject>

       ![Digite seu Nome de Usuário](../media/sc900-image-1.png)

3. Em seguida, forneça sua senha:

   - **Senha:** <inject key="AzureAdUserPassword"></inject>

       ![Digite sua Senha](../media/sc900-image-2.png)

4. Se for solicitado para permanecer conectado, você pode clicar em "Não."

5. Se uma janela pop-up **Bem-vindo ao Microsoft Azure** aparecer, simplesmente clique em **Cancelar** para pular o tour.

6. Clique em "Próximo" no canto inferior direito para começar sua jornada no laboratório!

    ![Comece sua Jornada no Azure](../media/sc900-image(3).png)

Este laboratório o capacitará com as habilidades para implantar e personalizar modelos Azure OpenAI, permitindo-lhe criar aplicações avançadas de IA, como chatbots e sistemas de recomendação.

## Contato de Suporte

A equipe de suporte do CloudLabs está disponível 24/7, 365 dias por ano, via e-mail e chat ao vivo para garantir assistência contínua a qualquer momento. Oferecemos canais de suporte dedicados especificamente para aprendizes e instrutores, garantindo que todas as suas necessidades sejam prontamente e eficientemente atendidas.

Contatos de Suporte para Aprendizes:

- Suporte por E-mail: labs-support@spektrasystems.com
- Suporte por Chat ao Vivo: https://cloudlabs.ai/labs-support

Agora, clique em Próximo no canto inferior direito para passar para a próxima página.

## Boas Aprendizado!!
