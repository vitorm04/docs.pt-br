---
title: Específicos de recurso do Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: 4b9a9c5c6395ed27845c8b618e49150a02aa3bda
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721847"
---
# <a name="windows-workflow-foundation-feature-specifics"></a>Específicos de recurso do Windows Workflow Foundation

[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] adiciona um número de recursos a Windows Workflow Foundation. Este documento descreve um número de recursos novos, e fornece detalhes sobre cenários em que podem ser úteis.

## <a name="messaging-activities"></a>Atividades de mensagem

As atividades de mensagens (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.ReceiveReply>) são usados para enviar e receber mensagens do WCF de fluxo de trabalho. <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> atividades são usadas para formar uma operação de serviço do Windows Communication Foundation (WCF) que é exposta por meio de WSDL, assim como os serviços web WCF padrão. <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> são usados para consumir um serviço web, semelhante a um WCF <xref:System.ServiceModel.ChannelFactory>; um **Add Service Reference** experiência também existe para o Workflow Foundation que gera atividades pré-configurados.

### <a name="getting-started-with-messaging-activities"></a>Guia de introdução com atividades de mensagem

- No Visual Studio 2012, crie um projeto de aplicativo de serviço de fluxo de trabalho do WCF. Um par de <xref:System.ServiceModel.Activities.Receive> e de <xref:System.ServiceModel.Activities.SendReply> será colocado na tela.

- Clique com botão direito no projeto e selecione **adicionar referência de serviço**. Aponte para um WSDL do serviço web existente e clique em **Okey**. Criar seu projeto para mostrar as atividades gerados (implementadas usando <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply>) em sua caixa de ferramentas.

- [Documentação dos serviços de fluxo de trabalho](../wcf/feature-details/workflow-services.md)

### <a name="messaging-activities-example-scenario"></a>Cenário exemplo de atividades de mensagem

Um `BestPriceFinder` serviço chama a vários serviços de companhia aérea para localizar o melhor preço de tíquete para uma rota específica. Implementar esse cenário exige que você usar as atividades de mensagem para receber a solicitação de preço, recuperar os preços serviços back-end e responder à solicitação do preço com o melhor preço. Ele também exigiria que você usar outras atividades de out-of-box para criar a lógica de negócios para calcular o melhor preço.

## <a name="workflowservicehost"></a>WorkflowServiceHost

O <xref:System.ServiceModel.WorkflowServiceHost> é o host de fluxo de trabalho que dá suporte a várias instâncias, configuração e mensagens do WCF (embora os fluxos de trabalho não é necessários usar o sistema de mensagens para ser hospedado). Ele também se integra com persistência, acompanhamento e controle de instância por meio de um conjunto de comportamentos de serviço. Assim como do WCF <xref:System.ServiceModel.ServiceHost>, o <xref:System.ServiceModel.WorkflowServiceHost> pode ser auto-hospedado em um aplicativo de console/WinForms/WPF ou o serviço do Windows ou hospedado na web (como um arquivo. xamlx) no IIS ou WAS.

### <a name="getting-started-with-workflow-service-host"></a>Guia de introdução com host de Serviço de Fluxo de Trabalho

- No Visual Studio 2010, crie um projeto de aplicativo de serviço de fluxo de trabalho do WCF: este projeto será configurado para usar <xref:System.ServiceModel.WorkflowServiceHost> em um ambiente de host da web.

- Para hospedar um fluxo de trabalho de não mensagem, adicione <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> personalizado que criará a instância com base em uma mensagem.

- Instâncias de fluxo de trabalho podem ser controladas (por exemplo, suspensa ou encerrado) adicionando um <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> para o <xref:System.ServiceModel.WorkflowServiceHost> e, em seguida, usando um <xref:System.ServiceModel.Activities.WorkflowControlClient>.

- Para Exemplos <xref:System.ServiceModel.WorkflowServiceHost> pode ser encontrado nas seções a seguir:

    - [Execução](./samples/execution.md)

    - Aplicativo: [Gerenciamento suspenso da instância](./samples/suspended-instance-management.md)

- [Visão geral dos serviços de fluxo de trabalho de hospedagem](../wcf/feature-details/hosting-workflow-services-overview.md)

### <a name="workflowservicehost-scenario"></a>Cenário de WorkflowServiceHost

Um serviço de BestPriceFinder chama a vários serviços de companhia aérea para localizar o melhor preço de tíquete para uma rota específica. Implementar esse cenário exige que você hospedar o fluxo de trabalho <xref:System.ServiceModel.WorkflowServiceHost>. Ele também seria usar as atividades de mensagem para receber a solicitação de preço, recuperar os preços serviços back-end e responder à solicitação do preço com o melhor preço.

## <a name="correlation"></a>Correlação

Uma correlação é uma das duas coisas:

- Uma maneira de mensagens de agrupamento juntos; ou seja, a relação entre uma mensagem de solicitação e sua resposta.

- Uma maneira para mapear uma parte de dados a uma instância de serviço

### <a name="getting-started"></a>Guia de Introdução

- Para começar com correlação, crie um novo projeto no Visual Studio. Crie uma variável do tipo <xref:System.ServiceModel.Activities.CorrelationHandle>.

- Um exemplo de correlação usado para agrupar mensagens seja adjacente uma correlação de solicitação de resposta que agrupe mensagens juntos.

    - Em um <xref:System.ServiceModel.Activities.Receive> atividade, clique em de <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> propriedade e adicione um <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> usando o CorrelationHandle criado na primeira etapa acima.

    - Criar uma <xref:System.ServiceModel.Activities.SendReply> atividade clicando com o <xref:System.ServiceModel.Activities.Receive> e clicando em "Criar SendReply". Cole-o no fluxo de trabalho após a atividade de <xref:System.ServiceModel.Activities.Receive> .

- Um exemplo de mapear uma parte de dados a uma instância do serviço é correlação conteudo base que mapeia um conjunto de dados (por exemplo, um ID de ordem) para uma determinada instância de fluxo de trabalho.

    - Em quaisquer atividades de mensagem, clique na propriedade de `CorrelationInitializers` e adicione <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> usando a variável de <xref:System.ServiceModel.Activities.CorrelationHandle> criado anterior. Clique duas vezes na propriedade desejada na mensagem (por exemplo, OrderID) no menu suspenso. Defina a propriedade de `CorrelatesWith` à variável de <xref:System.ServiceModel.Activities.CorrelationHandle> usado anterior.

- [Documentação conceitual de correlação](../wcf/feature-details/correlation.md)

### <a name="correlation-scenario"></a>Cenário de correlação

Um fluxo de trabalho de processamento de pedidos é usado para lidar com a criação do novo pedido e atualizar os pedidos existentes que estão em processo. Implementar esse cenário exige que você hospedar o fluxo de trabalho <xref:System.ServiceModel.WorkflowServiceHost> e usar as atividades de mensagem. Ele também exigiria a correlação com base no `orderId` para garantir que as atualizações são feitas ao fluxo de trabalho correto.

## <a name="simplified-configuration"></a>Configuração simplificada

O esquema de configuração do WCF é complexo e fornece aos usuários muitos recursos dificeis de localizar. No [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], nos concentramos em ajudar os usuários do WCF a configurarem os serviços com os seguintes recursos:

- Eliminando a necessidade para a configuração explícita por serviço. Se você não configurar qualquer \<service > elementos para seu serviço e o serviço não definir programaticamente qualquer ponto de extremidade e, em seguida, um conjunto de pontos de extremidade será adicionado automaticamente ao seu serviço, um endereço básico de serviço e por contrato implementado pelo serviço.

- Permite que o usuário para definir valores padrão para associações e comportamentos de WCF, que serão aplicados aos serviços sem a configuração explícita.

- Os pontos de extremidade padrão definem pontos de extremidade pré-configurados reutilizáveis, que têm valores fixos para uma ou mais propriedades de ponto de extremidade (endereço, associação e contrato), e reservam-nos definir propriedades personalizadas.

- Por fim, o <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> permite que você faça o gerenciamento centralizado de configuração do cliente do WCF, útil em cenários de configuração é selecionada ou alterada após o tempo de carregamento de domínio do aplicativo.

### <a name="getting-started"></a>Guia de Introdução

- [Um guia do desenvolvedor a WCF 4,0](https://go.microsoft.com/fwlink/?LinkId=204940)

- [Fábrica de canais de configuração](https://go.microsoft.com/fwlink/?LinkId=204941)

- [Elemento de ponto de extremidade padrão](https://go.microsoft.com/fwlink/?LinkId=204942)

- [Serviço melhorias de configuração no .net Framework 4](https://go.microsoft.com/fwlink/?LinkId=204943)

- [Erro de usuário comum no .NET 4: Mistyping o nome de configuração de serviço do WCF/WF](https://go.microsoft.com/fwlink/?LinkId=204944)

### <a name="simplified-configuration-scenarios"></a>Cenários simplificados de configuração

- Um desenvolvedor experiente ASMX deseja iniciar usando o WCF. No entanto, o WCF parece muito complicado! Que é todas essas informações que eu preciso de gravar em um arquivo de configuração? Em .NET 4, você ainda pode decidir não ter um arquivo de configuração de qualquer.

- Um conjunto existente de serviços WCF é muito difícil de configurar e manter. O arquivo de configuração possui milhares de linhas de código XML que são bastante perigosas para tocar. Ajuda é necessária para reduzir a quantidade de código para algo manejável.

## <a name="data-contract-resolver"></a>Resolução do contrato de dados

No .NET 3.5, houve algumas limitações no design de tipos conhecidas:

- Adicionar tipos conhecidos dinamicamente, durante a serialização desserialização, ou não foi possível.

- Os serializadores não pode manipular informações desconhecida de xsi:type .

- Não foi possível que usuários especificar que xsi:type de deseja ou não ter aparecer no fio, por exemplo, faça o tamanho de uma instância de serialização no fio menor.

O [DataContractResolver](../wcf/samples/datacontractresolver.md) resolve esses problemas no .NET 4.5.

### <a name="getting-started"></a>Guia de Introdução

- [Documentação da API do resolvedor de contrato de dados](https://go.microsoft.com/fwlink/?LinkId=204946)

- [Apresentando o resolvedor de contrato de dados](https://go.microsoft.com/fwlink/?LinkId=204947)

- Exemplos:

    - [DataContractResolver](../wcf/samples/datacontractresolver.md)

    - [KnownAssemblyAttribute](../wcf/samples/knownassemblyattribute.md)

### <a name="data-contract-resolver-scenarios"></a>Cenários de resolução do contrato de dados

- Evitar ter que declarar <xref:System.Runtime.Serialization.KnownTypeAttribute> de dez objetos em um serviço.

- Reduzindo o tamanho da operação XML.

## <a name="flowchart"></a>Fluxograma

O fluxograma é um paradigma conhecido para representar visualmente problemas de domínio. É um novo estilo de fluxo de controle nós estamos apresentando em .NET 4. Uma característica principal do fluxograma é que apenas uma atividade é executada em um determinado momento. Os fluxogramas podem expressar loop e resultados alternativos, mas não podem expressar nativo a execução simultânea de vários nós.

### <a name="getting-started"></a>Guia de Introdução

- No Visual Studio 2012, crie um aplicativo de console do fluxo de trabalho. Adicione um fluxograma no designer de fluxo de trabalho.

- O recurso de fluxograma usa as seguintes classes:

    - <xref:System.Activities.Statements.Flowchart>

    - <xref:System.Activities.Statements.FlowNode>

    - <xref:System.Activities.Statements.FlowDecision>

    - <xref:System.Activities.Statements.FlowStep>

    - <xref:System.Activities.Statements.FlowSwitch%601>

- Exemplos:

    - [Tratamento de falha em uma atividade do fluxograma usando TryCatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

    - [Processo de contratação](./samples/hiring-process.md)

- Documentação do designer:

    - [Designers de atividade de fluxograma](/visualstudio/workflow-designer/flowchart-activity-designers)

### <a name="flowchart-scenarios"></a>Cenários do fluxograma

Uma atividade do fluxograma pode ser usada para implementar um jogo de estimativa. O jogo de estimativa é muito simples: o computador seleciona um número aleatório e o jogador tem que descobrir esse número. Quando o jogador enviar cada estimativa, mostra do computador ele uma dica (ou seja, "Tente um número menor"). Se o jogador localiza o número em menos de 7 tentativas, ele recebe uma parabéns especiais do computador. Esse kit pode ser implementado com uma combinação das seguintes atividades procedurais:

- <xref:System.Activities.Statements.Sequence>

- <xref:System.Activities.Statements.While>

- <xref:System.Activities.Statements.Switch%601>

- <xref:System.Activities.Statements.TryCatch>

- <xref:System.Activities.Statements.Assign%601>

- <xref:System.Activities.Statements.If>

## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a>Atividades procedurais (sequência, se, ForEach, alterne, atribui, DoWhile, quando)

As atividades procedurais fornecem um mecanismo para o fluxo de controle em um modelo usando os conceitos que são familiares para programadores. Essas atividades permitem compilações de linguagem de programação tradicional estruturadas e, quando apropriado, fornecem a paridade de linguagem com idiomas procedurais comuns como C#/VB.

### <a name="getting-started"></a>Guia de Introdução

- No Visual Studio 2012, crie um aplicativo de console do fluxo de trabalho. Adicione atividades procedurais no designer de fluxo de trabalho.

- Exemplos:

    - [Processo de contratação](./samples/hiring-process.md)

    - [Processo de compra corporativo](./samples/corporate-purchase-process.md)

- Documentação do designer:

    - [Designer de atividade Parallel](/visualstudio/workflow-designer/parallel-activity-designer)

    - [ParallelForEach\<T > Designer de atividade](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)

### <a name="procedural-activity-scenarios"></a>Cenários procedurais de atividades

- <xref:System.Activities.Statements.Parallel>: Um sistema de gerenciamento de documentos de intranet tem um fluxo de trabalho de aprovação de documento. Documentos precisam ser aprovados por pessoas em vários departamentos antes que eles sejam publicado a intranet. Não há um ordem estabelecida para as aprovações; elas podem ocorrer a qualquer momento enquanto o documento está na fase de "aprovação pendente". Quando um usuário envia um documento para revisão deve ser aprovada por seu gerente direto, pelo administrador intranet, e pelo gerenciador interno de comunicação.

- <xref:System.Activities.Statements.ParallelForEach%601>: Um aplicativo de WF gerencia compras corporativos dentro de uma grande empresa. As regras corporativos determina que planejando antes que qualquer operação de compras, as avaliações de três fornecedores diferentes são necessárias. Um funcionário do departamento de compra seleciona três fornecedores de lista do fornecedor de empresa. Depois que esses fornecedores foram selecionados e notificados, a empresa esperará suas propostas econômicas. As propostas podem vie em qualquer ordem. Para implementar esse cenário em WF, usamos <xref:System.Activities.Statements.ParallelForEach%601> que iterará através da coleção de fornecedores e solicitará suas propostas econômicas. As oferece são coletadas completos, melhor é selecionado e exibido.

## <a name="invokemethod"></a>InvokeMethod

A atividade de <xref:System.Activities.Statements.InvokeMethod> reserva chamar métodos públicos em objetos ou no escopo. Suporta chamar métodos de instância e estática com ou sem parâmetros (que incluem matrizes de parâmetros), e métodos genéricos. Também permite executar o método forma síncrona e de forma assíncrona.

### <a name="getting-started"></a>Guia de Introdução

- No Visual Studio 2012, crie um aplicativo de console do fluxo de trabalho. Adicione uma atividade de <xref:System.Activities.Statements.InvokeMethod> no designer de fluxo de trabalho, e configurar métodos estáticos e de instância nele.

- Documentação do designer: [Designer de atividade de InvokeMethod](/visualstudio/workflow-designer/invokemethod-activity-designer)

### <a name="invokemethod-scenarios"></a>Cenários de InvokeMethod

- Um método em um objeto no escopo precisa ser chamado. Por exemplo, um valor precisa ser adicionado a um dicionário. Adicione o método de instância do dicionário é invocado, e a chave e o valor é fornecido.

- Um método precisa ser chamado em um objeto CLR herdado. Em vez de criar uma atividade personalizado para envolver a chamada à classe herdado, se estiver no escopo durante a execução de fluxo de trabalho, <xref:System.Activities.Statements.InvokeMethod> pode ser usado.

## <a name="error-handling-activities"></a>Atividades de tratamento de erro

A atividade de <xref:System.Activities.Statements.TryCatch> fornece um mecanismo para capturar exceções que ocorrem durante a execução de um conjunto de atividades contidas (semelhante à compilação try/catch em C#/VB). <xref:System.Activities.Statements.TryCatch> fornece tratamento de exceção a nível de fluxo de trabalho. Quando uma exceção não tratada é lançada, o fluxo de trabalho está anuladas e o bloco finally não será executado. Esse comportamento é consistente com o C#.

### <a name="getting-started"></a>Guia de Introdução

- No Visual Studio 2012, crie um aplicativo de console do fluxo de trabalho. Adicione uma atividade de <xref:System.Activities.Statements.TryCatch> no designer de fluxo de trabalho.

- Amostra: [Tratamento de falha em uma atividade do fluxograma usando TryCatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

- Documentação do designer: [Designers de atividade de tratamento de erro](/visualstudio/workflow-designer/error-handling-activity-designers)

### <a name="error-handling-scenarios"></a>Cenários de manipulação de erro

Um conjunto de atividades precisa ser executado, e a lógica específica precisa ser executada quando ocorre um erro. Se durante essa lógica de tratamento de erros que se encontra o erro é não recuperável, a exceção será rethrown, e a atividade pai (ou o host) manipulará o problema.

## <a name="pick-activity"></a>Atividade de picareta

A atividade de <xref:System.Activities.Statements.Pick> fornece o fluxo de controle baseado em que modela WF. <xref:System.Activities.Statements.Pick> contém várias ramificações onde cada ramificação espera um determinado evento ocorra antes de executar. Nessa configuração, <xref:System.Activities.Statements.Pick> se comporta semelhante a <xref:System.Activities.Statements.Switch%601> que a atividade será executado somente de um conjunto de eventos que está escuta. Cada ramificação é causado evento e o evento que ocorre executa a ramificação correspondente primeiro. Quaisquer outras ramificações cancelarem e param de ouvir eventos.

### <a name="getting-started"></a>Guia de Introdução

- No Visual Studio 2012, crie um aplicativo de console do fluxo de trabalho. Adicione uma atividade de <xref:System.Activities.Statements.Pick> no designer de fluxo de trabalho.

- Amostra: [Usando a atividade de Pick](./samples/using-the-pick-activity.md)

- Documentação do Designer: [Designer de atividade Pick](/visualstudio/workflow-designer/pick-activity-designer)

### <a name="pick-scenario"></a>Cenário de picareta

Um usuário precisa ser solicitado para a entrada. Em circunstâncias normais, o desenvolvedor usaria uma chamada de método como <xref:System.Console.ReadLine%2A> para solicitar a entrada de um usuário. O problema com essa configuração é que o programa espera até que o usuário digite algo. Nesse cenário, um tempo limite é necessário desbloquear uma atividade de bloqueio. Um cenário comum é um que requer uma tarefa ser concluído em uma determinada duração de tempo. Tempo para fora uma atividade de bloqueio é um cenário onde a picareta adicionar muito valor.

## <a name="wcf-routing-service"></a>WCF que requer o serviço

O serviço de roteamento é projetado para ser um roteador que permite que você controle como as mensagens do WCF fluem entre os clientes e serviços de software genérico. O serviço de roteamento permite que você a separar seus clientes de seus serviços, que lhe dá muito mais liberdade em termos de configurações que você pode dar suporte e a flexibilidade que você precisa ao considerar como hospedar seus serviços. No .NET 3.5, os clientes e serviços foram acoplados; um cliente tinha que conhecer todos os serviços que ele necessário para se comunicar com e onde eles foram localizados. Além disso, WCF dentro. .NET Framework 3,5 tinha as seguintes restrições:

- Manipulação de erro foi complexo, como essa lógica tinha que ser embutido no cliente.

- Os clientes e serviços tinham que sempre usar as mesmas associações.

- Os serviços foram raramente bom acrescentado: é mais fácil ter a conversa de cliente a um serviço que implementa todos, em vez de precisando de escolher entre vários serviços.

O serviço de roteamento dentro. A rede 4 é criada para facilitar resolver esses problemas. O novo serviço de roteamento possui os seguintes recursos:

1. O conteúdo do roteamento (os objetos de<xref:System.ServiceModel.Dispatcher.MessageFilter> examinar uma mensagem para determinar onde deve ser enviada.)

2. Compilação de uma ponte sobre o protocolo (mensagem & de transporte)

3. Tratamento de erros (o roteador captura exceções de comunicação e efetua o failover para pontos de extremidade alternativos)

4. (Na memória) atualização dinâmica de <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> e configuração de roteamento.

### <a name="getting-started"></a>Guia de Introdução

1. Documentação: [Roteamento](../wcf/feature-details/routing.md)

2. Exemplos: [Serviços de roteamento &#91;exemplos do WCF&#93;](../wcf/samples/routing-services.md)

3. Blog: [Regras de roteamento!](https://go.microsoft.com/fwlink/?LinkId=204956)

### <a name="routing-scenarios"></a>Cenários de roteamento

O serviço de roteamento é útil nas seguintes situações:

- Os clientes podem falar a vários serviços sem ter que evitá-los diretamente todos.

- Os clientes podem executar lógica adicional em uma solicitação de cliente determinar onde rotear-la

- Decompor as operações que um cliente é executado em várias implementações de serviço sem refatoração o cliente.

- Os clientes e serviços podem falar associações diferentes com as configurações de segurança diferentes.

- Os clientes podem ser ativados para ser mais robustos contra a falhar ou a indisponibilidade de serviços.

## <a name="wcf-discovery"></a>Descoberta de WCF

Descoberta do WCF é uma tecnologia de estrutura que permite incorporar um mecanismo de descoberta para a infraestrutura do aplicativo. Você pode usar esse para fazer o serviço para descobrir, e configurar seus clientes para procurar pelos serviços. Os clientes não precisam ser codificados difícil com ponto final, fazendo seu aplicativo mais robusta e tolerante falha. A descoberta é a plataforma perfeita para compilar recursos de uma configuração em seu aplicativo.

O produto é construído sobre o padrão de WS- descoberta. Criou para ser interoperável, extensível, e genérica. O modo de apoios ao produto dois de operação:

1. Gerenciado: onde há uma entidade na rede conhecedoa sobre serviços existentes, os clientes consultar-la diretamente para informações. Isso é análogo a Ative Directory.

2. Ad hoc: onde mensagens multicast de clientes usam localizar serviços.

Além disso, as mensagens de descoberta são protocolo de rede desconhecido; você pode usá-los em superior qualquer protocolo que oferecer suporte aos requisitos de modo. Por exemplo, a descoberta mensagens de multicast podem ser enviadas por canal de UDP ou qualquer outra rede que dá suporte a mensagens de multicast. Esses pontos, combinados com a flexibilidade de recursos, permitem que você se adapta a descoberta especificamente à sua solução de design.

### <a name="getting-started"></a>Guia de Introdução

- Documentação: [Descoberta do WCF](../wcf/feature-details/wcf-discovery.md)

- Exemplos: [Descoberta (exemplos)](../wcf/samples/discovery-samples.md)

### <a name="discovery-scenarios"></a>Cenários de descoberta

Um desenvolvedor não deseja para pontos de extremidade difícil de código, desde que é conhecido quando serviço my estão disponíveis. Em vez disso, o desenvolvedor deseja escolha um serviço em tempo de execução. Mais desacoplar, vigor, e uma configuração são necessários entre os componentes no aplicativo.

## <a name="tracking"></a>Acompanhamento

Controle de fluxo de trabalho fornece informações sobre a execução de uma instância de fluxo de trabalho. Os eventos de rastreamento são emitidos do fluxo de trabalho no nível da instância de fluxo de trabalho e as atividades no fluxo de trabalho são executadas. Um participante de acompanhamento de fluxo de trabalho precisa ser adicionado ao host de fluxo de trabalho para assinar a acompanhar registros. Os registros de rastreamento são filtrados utilizando um perfil de rastreamento. . Framework .NET fornece um participante de rastreamento (ETW de rastreamento do Windows), e um perfil básico é instalado no arquivo machine.config.

### <a name="getting-started"></a>Guia de Introdução

1. No Visual Studio 2010, crie um projeto de aplicativo de serviço de fluxo de trabalho do WCF. Um par de <xref:System.ServiceModel.Activities.Receive> e de <xref:System.ServiceModel.Activities.SendReply> será colocado na tela para o início.

2. Abra o web.config e adicionar um comportamento de rastreamento de ETW sem o perfil.

    1. O perfil padrão é usado.

    2. Abra o Visualizador de eventos e habilitar o canal analítico no seguinte nó: **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**, **aplicativos de servidor**. Clique com botão direito **analítico** e selecione **Habilitar Log**.

    3. Execute o serviço de fluxo de trabalho.

    4. Observe os eventos de rastreamento de fluxo de trabalho no visualizador de eventos.

3. Exemplos: [Acompanhamento](./samples/tracking.md)

4. Documentação conceitual: [Acompanhamento e rastreamento de fluxo de trabalho](workflow-tracking-and-tracing.md)

## <a name="sql-workflow-instance-store"></a>Store instância de fluxo de trabalho do SQL

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> é uma implementação com base no servidor SQL de um armazenamento de instância. Um armazenamento de instância armazena o estado de uma instância em execução junto com todos os dados necessários carregar e continuar essa instância. O host serviço instrui o armazenamento de instância para salvar o estado da instância se o fluxo de trabalho persistir, e instrui o armazenamento de instância para carregar o estado da instância quando uma mensagem chega para essa instância ou uma atividade do atraso expira.

### <a name="getting-started"></a>Guia de Introdução

1. No Visual Studio 2012, crie um fluxo de trabalho que contém um implícita ou explícita <xref:System.Activities.Statements.Persist> atividade. Adicionar o comportamento de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> ao seu host serviço de fluxo de trabalho. Isso pode ser feito no código ou no arquivo de configuração do aplicativo.

2. Exemplos: [Persistência](./samples/persistence.md)

3. Documentação conceitual: [Store de instância de fluxo de trabalho do SQL](sql-workflow-instance-store.md).
