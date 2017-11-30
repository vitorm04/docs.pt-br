---
title: "Criando um aplicativo orientado por microsserviço"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Criando um aplicativo orientado por microsserviço"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1e1dc919c7e35580576c86b4cf9872b4f8cea2c2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="designing-a-microservice-oriented-application"></a>Criando um aplicativo orientado por microsserviço

Esta seção se concentra no desenvolvimento de um aplicativo empresarial hipotético do lado do servidor.

## <a name="application-specifications"></a>Especificações de aplicativo

O aplicativo hipotético manipula solicitações pela execução de lógica de negócios, acessar bancos de dados e, em seguida, retornar respostas HTML, JSON ou XML. Podemos dirá que o aplicativo deve oferecer suporte a uma variedade de clientes, incluindo navegadores de desktop executando aplicativos de página única (SPAs), aplicativos web tradicionais, aplicativos web móveis e aplicativos móveis nativo. O aplicativo também pode expor uma API de terceiros podem consumir. Ele também deve ser capaz de integrar seu microservices ou aplicativos externos de forma assíncrona, para que a abordagem ajudará a resiliência de microservices no caso de falhas parciais.

O aplicativo consistirá esses tipos de componentes:

-   Componentes de apresentação. Esses são responsáveis por gerenciar a interface do usuário e o consumo de serviços remotos.

-   Lógica de negócios ou de domínio. Isso é a lógica do domínio do aplicativo.

-   Lógica de acesso a banco de dados. Isso consiste em componentes de acesso de dados responsável para acessar bancos de dados (SQL ou NoSQL).

-   Lógica de integração do aplicativo. Isso inclui um canal de mensagens, principalmente com base em agentes de mensagens.

O aplicativo exigirá alta escalabilidade, permitindo que seus subsistemas verticais de expansão de forma independente, pois determinados subsistemas exigirá mais escalabilidade que outras pessoas.

O aplicativo deve ser capaz de ser implantado em vários ambientes de infraestrutura (várias nuvens públicas e locais) e idealmente deve ser capaz de mover facilmente do Linux para Windows (ou vice-versa), de plataforma cruzada.

## <a name="development-team-context"></a>Contexto da equipe de desenvolvimento

Pressupõe-se também o seguinte sobre o processo de desenvolvimento para o aplicativo:

-   Você tem várias equipes de desenvolvimento com foco em diferentes áreas de negócios do aplicativo.

-   Novos membros da equipe devem se tornarem rapidamente produtivos, e o aplicativo deve ser fácil de entender e modificar.

-   O aplicativo terá uma evolução de longo prazo e constantes de regras de negócio.

-   Você precisa de boa manutenção a longo prazo, que significa ter agilidade ao implementar as novas alterações no futuro e conseguir atualizar vários subsistemas com impacto mínimo sobre os outros subsistemas.

-   Você deseja integração contínua prática e implantação contínua do aplicativo.

-   Você deseja tirar proveito das tecnologias emergentes (estruturas, linguagens de programação e etc.) durante a evolução do aplicativo. Você não deseja fazer migrações completas do aplicativo ao mover para novas tecnologias, como o que poderia resultar em custos e afetar a previsibilidade e a estabilidade do aplicativo.

## <a name="choosing-an-architecture"></a>Escolha uma arquitetura

O que deve ser a arquitetura de implantação de aplicativo? As especificações para o aplicativo, junto com o contexto de desenvolvimento altamente recomendável que você deve projetar o aplicativo decompõe-lo em subsistemas autônomos na forma de colaboração microservices e contêineres, onde um microsserviço é um contêiner.

Nessa abordagem, cada serviço (contêiner) implementa um conjunto de funções coesos e restrito relacionados. Por exemplo, um aplicativo pode consistir de serviços como o serviço de catálogo, ordenação service, serviço de carrinho, serviço de perfil de usuário, etc.

Microservices se comunicar usando protocolos como HTTP (REST), mas também de forma assíncrona (ou seja, AMQP) sempre que possível, especialmente quando propagar atualizações com eventos de integração.

Microservices são desenvolvidos e implantados como contêineres independentemente uma da outra. Isso significa que uma equipe de desenvolvimento pode desenvolver e implantar um determinado microsserviço sem afetar outros subsistemas.

Cada microsserviço tem seu próprio banco de dados, permitindo que ele seja totalmente separada dos outros microservices. Quando necessário, a consistência entre bancos de dados de diferentes microservices é obtida usando eventos de integração do nível do aplicativo (por meio de um barramento de evento lógico) tratados no comando e consulta responsabilidade CQRS (segregação). Por isso, as restrições de negócios devem adotar consistência eventual entre os vários microservices e bancos de dados relacionados.

### <a name="eshoponcontainers-a-reference-application-for-net-core-and-microservices-deployed-using-containers"></a>eShopOnContainers: um aplicativo de referência para .NET Core e microservices implantados usando contêineres

Para que você possa focalizar a arquitetura e as tecnologias em vez de pensar em um domínio de negócios hypothetic que você talvez não saiba, selecionamos um domínio de negócios conhecido — ou seja, um aplicativo simplificado comércio eletrônico (e-loja) que apresenta um catálogo de produtos, usa pedidos de clientes, verifica o estoque e executa outras funções de negócios. Código-fonte neste aplicativo com base em contêiner está disponível na [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) repositório GitHub.

O aplicativo consiste em vários subsistemas, incluindo várias repositório da interface do usuário front-ends (um aplicativo Web e um aplicativo móvel nativo), junto com o back-end microservices e contêineres para todas as operações do servidor necessários. Figura 8-1 mostra a arquitetura do aplicativo de referência.

![](./media/image1.png)

**Figura 8-1**. Os eShopOnContainers Referência de aplicativo, mostrando uma comunicação de cliente para microsserviço direta e o barramento de evento

**Ambiente de hospedagem**. Na Figura 8-1, você verá vários contêineres implantados em um único host do Docker. Isso seria o caso durante a implantação em um único host do Docker com o docker-compor o comando. No entanto, se você estiver usar um orquestrador ou cluster de contêiner, cada contêiner pode ser executado em um host diferente (nó), e qualquer nó pode estar executando qualquer número de contêineres, como é explicado anteriormente na seção de arquitetura.

**Arquitetura de comunicação**. O aplicativo eShopOnContainers usa dois tipos de comunicação, dependendo do tipo da ação funcional (consultas e atualizações e transações):

-   Comunicação direta do cliente para microsserviço. Isso é usado para consultas e ao aceitar a atualização ou comandos transacionais dos aplicativos cliente.

-   Comunicação assíncrona com base em eventos. Isso ocorre por meio de um barramento de evento para propagar atualizações em microservices ou integrar aplicativos externos. O barramento de evento pode ser implementado com qualquer tecnologia de infraestrutura do agente de mensagens como RabbitMQ ou usando o nível mais alto barramentos de serviço como o Azure Service Bus, NServiceBus, MassTransit ou Brighter.

O aplicativo é implantado como um conjunto de microservices na forma de contêineres. Aplicativos cliente podem se comunicar com esses contêineres bem como a comunicação entre o microservices. Conforme mencionado, essa arquitetura inicial está usando uma arquitetura de comunicação de cliente para microsserviço direta, o que significa que um aplicativo cliente pode fazer solicitações a cada o microservices diretamente. Cada microsserviço tem um ponto de extremidade público como https://servicename.applicationname.companyname. Se necessário, cada microsserviço pode usar uma porta TCP diferente. Em produção, o que a URL deve mapear para o balanceador de carga dos microservices, que distribui solicitações entre as instâncias de microsserviço disponíveis.

**Observação importante sobre API Gateway vs. Comunicação direta no eShopOnContainers.** Conforme explicado na seção deste guia de arquitetura, a arquitetura de comunicação de cliente para microsserviço direta pode ter desvantagens quando você estiver criando um aplicativo baseado em microsserviço grande e complexo. Mas é bom o bastante para um pequeno aplicativo, como no eShopOnContainers iniciar o aplicativo, em que a meta é se concentrar em um guia simples aplicativo baseado no contêiner do Docker e não queremos criar um único API Gateway monolítico que podem afetar o autonomia de desenvolvimento dos microservices.

Mas, se você pretende criar um aplicativo baseado em microsserviço grande com dezenas de microservices, é altamente recomendável que você considere o padrão de Gateway de API, como é explicado na seção de arquitetura.
Essa decisão de arquitetura pode ser refatorado depois de pensar sobre aplicativos prontos para produção e fachadas feitos especialmente para clientes remotos. Ter vários Gateways de API personalizada dependendo do fator de forma de aplicativos cliente pode fornecer benefícios em termos de agregação de dados diferente por aplicativo cliente Além disso, você pode ocultar microservices interno ou APIs para os aplicativos cliente e autorizar nessa camada única. 

No entanto e, conforme mencionado, lembre-se em grande e monolítico Gateways de API que pode interromper a autonomia de desenvolvimento dos microservices.

### <a name="data-sovereignty-per-microservice"></a>Soberania dados por microsserviço

O aplicativo de exemplo, cada microsserviço possui seu próprio banco de dados ou fonte de dados e cada banco de dados ou fonte de dados é implantada como outro contêiner. Essa decisão de design foi feita apenas para tornar mais fácil para um desenvolvedor obter o código do GitHub, clone-o e abra-o no Visual Studio ou o código do Visual Studio. Ou, Alternativamente, torna mais fácil compilar imagens Docker personalizadas usando a CLI do .NET Core e a CLI do Docker e, em seguida, implantar e executá-los em um ambiente de desenvolvimento do Docker. De qualquer forma, usar contêineres para dados de fontes permite aos desenvolvedores criarem e implantar em questão de minutos sem a necessidade de provisionar um banco de dados externo ou qualquer outra fonte de dados com o disco rígidas dependências na infraestrutura (nuvem ou local).

Em um ambiente de produção real, de alta disponibilidade e escalabilidade, os bancos de dados devem ser baseados em servidores de banco de dados na nuvem ou local, mas não em contêineres.

Portanto, as unidades de implantação microservices (e até mesmo para bancos de dados neste aplicativo) são contêineres do Docker e o aplicativo de referência é um aplicativo de contêiner vários que adote microservices princípios.

### <a name="additional-resources"></a>Recursos adicionais

-   **eShopOnContainers repositório GitHub. Código do aplicativo de referência da fonte**
    *https://aka.ms/eShopOnContainers/*

## <a name="benefits-of-a-microservice-based-solution"></a>Benefícios de uma solução baseada em microsserviço

Uma solução de microsserviço com base em como isso traz muitos benefícios:

**Cada microsserviço for relativamente pequeno, fácil de gerenciar e desenvolver**. Especificamente:

-   É fácil para um desenvolvedor de entender e se familiarizar rapidamente com boa produtividade.

-   Contêineres início rápido, que faz com que os desenvolvedores mais produtivos.

-   Um IDE como Visual Studio pode carregar projetos menores rápidos, tornando-os desenvolvedores produtivos.

-   Cada microsserviço pode ser criado, desenvolvido e implantado independentemente de outros microservices, que fornece a agilidade porque é mais fácil de implantar novas versões do microservices com frequência.

**É possível expandir as áreas individuais do aplicativo**. Por exemplo, o serviço de catálogo ou o carrinho talvez precise ser expandida, mas não o processo de solicitação. Uma infraestrutura de microservices será muito mais eficiente em relação os recursos usados quando o dimensionamento de uma arquitetura monolítica seria.

**Você pode dividir o trabalho de desenvolvimento entre várias equipes**. Cada serviço pode ser propriedade de uma equipe de desenvolvimento único. Cada equipe pode gerenciar, desenvolver, implantar e dimensionar seu serviço, independentemente do restante das equipes.

**Problemas são mais isolados**. Se houver um problema em um serviço, somente esse serviço é inicialmente afetado (exceto quando o design errado é usado, com dependências diretas entre microservices) e outros serviços podem continuar a tratar as solicitações. Por outro lado, um componente com defeito em uma arquitetura de implantação monolítico pode colocar o sistema inteiro, especialmente quando envolve recursos, como um vazamento de memória. Além disso, quando um problema em um microsserviço for resolvido, você pode implantar apenas o microsserviço afetado sem afetar o restante do aplicativo.

**Você pode usar as tecnologias mais recentes**. Como você pode começar a desenvolver serviços de forma independente e executá-los lado a lado (graças contêineres e .NET Core), começar a usar as últimas tecnologias e estruturas expediently em vez de prisão em uma pilha ou a estrutura para todo o mais antigo aplicativo.

## <a name="downsides-of-a-microservice-based-solution"></a>Desvantagens de uma solução baseada em microsserviço

Uma solução de microsserviço com base em como isso também apresenta algumas desvantagens:

**Aplicativo distribuído**. Distribuir o aplicativo adiciona complexidade para desenvolvedores quando projetar e criar os serviços. Por exemplo, os desenvolvedores devem implementar interservice comunicação usando protocolos como HTTP ou AMPQ, que adiciona complexidade para teste e tratamento de exceção. Ele também adiciona latência ao sistema.

**Complexidade de implantação**. Um aplicativo que possui vários tipos de microservices e precisa de alta escalabilidade (ela precisa ser capaz de criar várias instâncias por serviço e equilibrar os serviços em vários hosts) significa um alto grau de complexidade de implantação para o gerenciamento e operações de TI. Se você não estiver usando uma infraestrutura e orientada a microsserviço (como um agendador e o orchestrator), essa complexidade adicional pode exigir que os esforços de desenvolvimento muito mais que o aplicativo de negócios.

**Transações atômicas**. Transações atômicas entre vários microservices geralmente não são possíveis. Os requisitos de negócios precisam adotar consistência eventual entre vários microservices.

**Aumentado necessidades de recursos globais** (total de memória, unidades e recursos de rede para todos os servidores ou hosts). Em muitos casos, quando você substituir um aplicativo monolítico com uma abordagem de microservices, a quantidade de recursos globais necessitados para o novo aplicativo com base em microsserviço será maior do que as necessidades de infraestrutura do aplicativo monolítico original. Isso ocorre porque o mais alto grau de granularidade e serviços distribuídos requer recursos mais globais. No entanto, o aumento do uso de recursos devido a baixo custo de recursos em geral e o benefício de poder expandir apenas determinadas áreas do aplicativo comparada aos custos de longo prazo quando desenvolvendo aplicativos monolíticos, é geralmente um bom equilíbrio para grandes aplicativos de longo prazo.

**Problemas com a comunicação direta client‑to‑microservice**. Quando o aplicativo é grande, com dezenas de microservices, existem desafios e limitações se o aplicativo exigir comunicações de cliente-para-microsserviço diretas. Um problema é uma potencial incompatibilidade entre as necessidades do cliente e as APIs expostas por cada o microservices. Em alguns casos, o aplicativo cliente precisará fazer muitas solicitações separadas para compor a interface do usuário, que pode ser ineficiente pela Internet e seria impraticável em uma rede móvel. Portanto, as solicitações do aplicativo cliente para o sistema de back-end devem ser minimizadas.

Outro problema com a comunicação de cliente para microsserviço direto é que algumas microservices usando protocolos não são amigável para a Web. Um serviço pode usar um protocolo binário, enquanto outro serviço pode usar o AMQP de mensagens. Esses protocolos não são firewall‑friendly e são melhor usados internamente. Normalmente, um aplicativo deve usar protocolos como HTTP e WebSockets para a comunicação fora do firewall.

Ainda outra desvantagem dessa abordagem client‑to‑service direto é que ele é difícil refatorar os contratos para os microservices. Ao longo do tempo, os desenvolvedores talvez queira alterar como o sistema está particionado em serviços. Por exemplo, eles podem mesclar dois serviços ou dividir um serviço em dois ou mais serviços. No entanto, se os clientes se comunicam diretamente com os serviços, executar esse tipo de refatoração pode quebrar a compatibilidade com aplicativos cliente.

Conforme mencionado na seção de arquitetura, ao projetar e criar um aplicativo complexo com base em microservices, você pode considerar o uso de vários Gateways API refinada em vez da abordagem mais simples de comunicação client‑to‑microservice direto.

**Particionamento de microservices**. Por fim, não importa qual abordagem para sua arquitetura de microsserviço, outro desafio é decidir como um aplicativo de ponta a ponta em vários microservices da partição. Conforme observado na seção do guia de arquitetura, há várias técnicas e abordagens que você pode executar. Basicamente, você precisa identificar áreas do aplicativo que é separado das outras áreas e que têm um número baixo de dependências de hardware. Em muitos casos, isso é alinhado ao particionamento de serviços pelo caso de uso. Por exemplo, em nosso aplicativo de loja e, temos um serviço de ordenação que é responsável por toda a lógica de negócios relacionada ao processo de ordem. Temos também o serviço de catálogo e o serviço de compras que implementam a outros recursos. Idealmente, cada serviço deve ter somente um pequeno conjunto de responsabilidades. Isso é semelhante para o princípio da responsabilidade única (SRP) aplicado a classes, que declara que uma classe deve ter somente uma razão para alterar. Mas nesse caso, ele é microservices, para que o escopo seja maior do que uma única classe. A maioria das todos, um microsserviço deve ser completamente autônoma, de ponta a ponta, incluindo a responsabilidade por suas próprias fontes de dados.

## <a name="external-versus-internal-architecture-and-design-patterns"></a>Externas e internas padrões de arquitetura e design

A arquitetura externa é composta por vários serviços, seguindo os princípios descritos na seção deste guia de arquitetura de arquitetura de microsserviço. No entanto, dependendo da natureza de cada microsserviço e independentemente da arquitetura de alto nível microsserviço você escolher, é comum e, às vezes, convém ter diferentes arquiteturas internas, cada um com base em padrões diferentes para diferentes microservices. O microservices pode até usar tecnologias diferentes e linguagens de programação. Figura 8-2 ilustra essa diversidade.

![](./media/image2.png)

**Figura 8-2**. Externas e interna arquitetura e design

Por exemplo, em nosso *eShopOnContainers* microservices de perfil de exemplo, o catálogo, carrinho e usuário são simples (basicamente, subsistemas CRUD). Portanto, sua arquitetura interna e design é simples. No entanto, você pode ter outros microservices, como o ordenação microsserviço, que é mais complexa e representa a constante mudança regras de negócios com um alto grau de complexidade do domínio. Em casos assim, talvez você queira implementar os padrões mais avançados dentro de um microsserviço específico, como as definidas com abordagens de design orientado a domínio (DDD), como estamos o *eShopOnContainers* ordenação microsserviço. (Analisaremos esses padrões DDD na seção posterior que explica a implementação do *eShopOnContainers* ordenação microsserviço.)

Outra razão para uma tecnologia diferente por microsserviço seria a natureza de cada microsserviço. Por exemplo, talvez seja melhor usar uma linguagem de programação funcional como F\#, ou uma linguagem como R, mesmo se estiver direcionando AI e domínios, em vez de uma linguagem de programação mais orientada a objeto como C de aprendizado de máquina\#.

O resultado é que cada microsserviço pode ter uma arquitetura interna diferente com base nos padrões de design diferentes. Microservices todos os não devem ser implementadas usando padrões avançados de DDD, porque que poderia ser excesso de engenharia-los. Da mesma forma, microservices complexas com lógica de negócios constantes não devem ser implementadas como componentes CRUD, ou você pode acabar com o código de baixa qualidade.



## <a name="the-new-world-multiple-architectural-patterns-and-polyglot-microservices"></a>O novo mundo: vários padrões de arquitetura e microservices polyglot

Há muitos padrões de arquitetura usados por desenvolvedores e arquitetos de software. A seguir estão algumas (combinação de estilos de arquitetura e padrões de arquitetura):

-   Simples CRUD, camada única, camada única.

-   [Tradicional em camadas N](https://msdn.microsoft.com/en-us/library/ee658109.aspx#Layers).

-   [Controlado por domínio Design em camadas N](https://blogs.msdn.microsoft.com/cesardelatorre/2011/07/03/published-first-alpha-version-of-domain-oriented-n-layered-architecture-v2-0/).

-   [Limpar arquitetura](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html) (conforme usado com [eShopOnWeb](http://aka.ms/WebAppArchitecture))

-   [Comando e consultar a segregação de responsabilidade](https://martinfowler.com/bliki/CQRS.html) (CQRS).

-   [Arquitetura orientada a eventos](https://en.wikipedia.org/wiki/Event-driven_architecture) (EDA).

Você também pode criar microservices com várias tecnologias e linguagens, como APIs da Web do ASP.NET Core, NancyFx, ASP.NET Core SignalR (disponível no .NET Core 2), F\#, Node.js, Python, Java, C++, GoLang e muito mais.

O ponto importante é que nenhum padrão de arquitetura em particular ou estilo nem qualquer tecnologia em particular, é ideal para todas as situações. A Figura 8-3 mostra algumas abordagens e tecnologias (embora não em nenhuma ordem específica) que pode ser usado em microservices diferentes.

![](./media/image3.png)

**Figura 8-3**. Padrões de arquitetura múltiplos e com o mundo microservices polyglot

Conforme mostrado na Figura 8-3, em aplicativos composta de muitos microservices (limitado contextos na terminologia de design controlado por domínio, ou simplesmente "subsistemas" como microservices autônomo), você pode implementar cada microsserviço de maneira diferente. Cada um pode ter um padrão de arquitetura diferente e usar idiomas diferentes e bancos de dados dependendo da natureza do aplicativo, requisitos de negócios e prioridades. Em alguns casos o microservices pode ser semelhante. Mas isso não é geralmente o caso, porque o limite de contexto e os requisitos de cada subsistema normalmente são diferentes.

Por exemplo, para um aplicativo simple de manutenção CRUD, ele não pode fazer sentido para projetar e implementar os padrões DDD. Mas, para seu negócio principal ou de domínio principal, você precisará aplicar os padrões mais avançados para lidar com a complexidade de negócios com constantes regras de negócio.

Especialmente ao lidar com grandes aplicativos compostos por vários subsistemas, você não deve aplicar uma única arquitetura de alto nível com base em um única arquitetura padrão. Por exemplo, a CQRS não deve ser aplicado como uma arquitetura de nível superior para todo o aplicativo, mas pode ser útil para um conjunto específico de serviços.

Não há nenhum marcador prata ou um padrão de arquitetura correta para cada caso específico. Você não pode ter "um padrão de arquitetura para eliminá-los." Dependendo de prioridades de cada microsserviço, você deve escolher uma abordagem diferente para cada uma, conforme explicado nas seções a seguir.


>[!div class="step-by-step"]
[Anterior] (index.md) [Avançar] (dados-controlada por-crud-microservice.md)
