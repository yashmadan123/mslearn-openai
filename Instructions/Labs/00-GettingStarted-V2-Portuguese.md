# Comece com o OpenAI e Construa Soluções de Linguagem Natural

### Duração Estimada Total: 4 Horas

## Visão Geral

O serviço Azure OpenAI traz os modelos de IA generativa desenvolvidos pela OpenAI para a plataforma Azure, permitindo o desenvolvimento de soluções de IA poderosas com a segurança, escalabilidade e integração dos serviços em nuvem do Azure. Neste laboratório, você aprenderá a provisionar o serviço Azure OpenAI como um recurso e usar o Azure OpenAI Studio para implementar e explorar os modelos da OpenAI. Com o Azure OpenAI, os desenvolvedores podem criar aplicações como chatbots e modelos de linguagem que se destacam na compreensão da linguagem humana natural. O serviço oferece acesso a modelos de IA pré-treinados e um conjunto de APIs e ferramentas para personalizar e ajustar esses modelos para atender aos requisitos específicos da aplicação. Neste cenário, você assumirá o papel de um desenvolvedor de software encarregado de implementar um aplicativo para fornecer recomendações de caminhadas usando IA generativa, demonstrando técnicas aplicáveis a qualquer aplicativo que utilize as APIs do Azure OpenAI.

## Objetivo

No final deste laboratório, você será capaz de:

- **Começar com o Azure OpenAI Service**: Este exercício prático visa provisionar um recurso Azure OpenAI e implementar um modelo. Explore as capacidades do modelo no playground de Completions, depois interaja com ele usando o playground de Chat. Ajuste as respostas ajustando prompts e parâmetros, e aproveite a geração de código para automatizar tarefas.
- **Usar os SDKs do Azure OpenAI na sua aplicação**: Este exercício prático visa provisionar um recurso de Azure OpenAI, implementar um modelo, configurar e configurar uma aplicação no Cloud Shell e, em seguida, executar a aplicação, demonstrando todo o ciclo de vida, desde a criação do recurso até a implementação e execução da aplicação.

## Pré-requisitos

- Familiaridade com o serviço Azure OpenAI, Azure CLI e APIs REST
- Compreensão básica de conceitos de IA e Machine Learning

## Arquitetura

O fluxo de arquitetura para esta tarefa começa com o provisionamento de um recurso Azure OpenAI em sua assinatura do Azure e a implementação de um modelo pré-treinado usando o Azure OpenAI Studio. Em seguida, você explorará as capacidades do modelo no playground de Completions e testará suas capacidades conversacionais no playground de Chat, experimentando diferentes prompts e parâmetros para personalizar as respostas. Você também investigará as capacidades de geração de código do modelo. Na fase de desenvolvimento da aplicação, você configurará seu ambiente no Azure Cloud Shell, configurará a aplicação para integrar com o modelo OpenAI implementado e, finalmente, executará a aplicação para fornecer recomendações de caminhadas usando IA generativa.

## Diagrama de Arquitetura

![Acesse sua VM e Guia do Laboratório](../media/arch20.png)

## Explicação dos Componentes

1. **Azure OpenAI**: O serviço de Azure OpenAI fornece acesso via API REST aos poderosos modelos de linguagem da OpenAI e esses modelos conseguem se integrar com seus dados, permitindo interações personalizadas e seguras.
2. **Modelos Azure OpenAI**: Oferece modelos de linguagem pré-treinados e personalizáveis para várias aplicações de IA. Esses modelos permitem soluções avançadas baseadas em IA gerando conteúdo adaptado e contextualmente relevante com base em prompts bem elaborados.
3. **Azure CloudShell**: O Azure CloudShell oferece uma experiência de shell integrada e baseada em navegador para gerenciar recursos do Azure. Ele fornece um ambiente pronto para uso com ferramentas pré-instaladas e acesso tanto ao Bash quanto ao PowerShell.

## Começando com o Laboratório

### Acessando a seu Ambiente de Laboratório

Uma vez pronto para começar, sua máquina virtual e o guia do laboratório estarão ao seu alcance diretamente no seu navegador web.

![Acesse sua VM e Guia do Laboratório](../media/labguide-1.png)

### Máquina Virtual & Guia do Laboratório

Sua máquina virtual é seu principal recurso durante o workshop. O guia do laboratório é seu roteiro para o sucesso.

### Explorando Seus Recursos de Laboratório

Para entender melhor seus recursos e credenciais de laboratório, navegue até a tab **Ambiente**.

![Explore os Recursos do Laboratório](../media/env-1.png)

### Utilizando o Recurso de Janela Dividida

Para conveniência, você pode abrir o tab do laboratório em uma janela separada selecionando o botão **Janela Dividida** no canto superior direito.

![Use o Recurso de Janela Dividida](../media/spl.png)

### Gerenciando Sua Máquina Virtual

Sinta-se à vontade para iniciar, parar ou reiniciar sua máquina virtual conforme necessário na tab **Recursos**. Sua experiência está nas suas mãos!

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

2. Você verá a tab **Entrar no Microsoft Azure**. Aqui, insira suas credenciais:

   - **Email/Usuário:** <inject key="AzureAdUserEmail"></inject>

       ![Digite seu Nome de Usuário](../media/sc900-image-1.png)

3. Em seguida, forneça sua senha/password:

   - **Senha:** <inject key="AzureAdUserPassword"></inject>

       ![Digite sua Senha](../media/sc900-image-2.png)

4. Se for solicitado para permanecer conectado, você pode clicar em "Não."

5. Se uma janela pop-up **Bem-vindo ao Microsoft Azure** aparecer, simplesmente clique em **Cancelar** para pular o tour.

6. Clique em "Próximo" no canto inferior direito para começar sua jornada no laboratório!

    ![Comece sua Jornada no Azure](../media/sc900-image(3).png)

Este laboratório o capacitará com as capacidades para implementar e personalizar modelos Azure OpenAI, permitindo-lhe criar aplicações avançadas de IA, como chatbots e sistemas de recomendação.

## Contato de Suporte

A equipe de suporte da CloudLabs está disponível 24/7, 365 dias por ano, via e-mail e chat para garantir assistência contínua a qualquer momento. Oferecemos canais de suporte dedicados especificamente para alunos e instrutores, garantindo que todas as suas necessidades sejam prontamente e eficientemente atendidas.

Contatos de Suporte para Alunos:

- Suporte por E-mail: labs-support@spektrasystems.com
- Suporte por Chat ao Vivo: https://cloudlabs.ai/labs-support

Agora, clique em Próximo no canto inferior direito para passar para a próxima página.

## Votos de bom treinamento!
