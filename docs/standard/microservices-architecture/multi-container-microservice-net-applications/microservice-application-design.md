---
title: Projetando um aplicativo orientado a microsserviços
description: Arquitetura de Microsserviços .NET para aplicativos .NET em contêineres | Entenda os benefícios e as desvantagens de um aplicativo orientado a microsserviços, para que você possa tomar uma decisão informada.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 8b2372ab5d58898b7a5730e118cc710d09a9bf92
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130488"
---
# <a name="designing-a-microservice-oriented-application"></a>Projetando um aplicativo orientado a microsserviços

Esta seção se concentra no desenvolvimento de um aplicativo empresarial hipotético do lado do servidor.

## <a name="application-specifications"></a>Especificações do aplicativo

O aplicativo hipotético lida com as solicitações por meio da execução de lógica de negócios, do acesso ao bancos de dados, retornando as respostas em HTML, JSON ou XML. Digamos que o aplicativo deve oferecer suporte a uma variedade de clientes, incluindo navegadores de área de trabalho que executam SPAs (aplicativos de página única), aplicativos Web tradicionais, aplicativos Web móveis e aplicativos móveis nativos. O aplicativo também deve expor uma API para ser consumida por terceiros. Ele também deve ser capaz de integrar seus microsserviços ou aplicativos externos de forma assíncrona, ajudando na resiliência dos microsserviços no caso de falhas parciais.

O aplicativo consistirá nesses tipos de componentes:

- Componentes de apresentação. Eles são responsáveis por gerenciar a interface do usuário e o consumo de serviços remotos.

- Lógica de negócios ou domínio. Essa é a lógica de domínio do aplicativo.

- Lógica de acesso a banco de dados. Consiste em componentes de acesso a dados responsáveis por acessar bancos de dados (SQL ou NoSQL).

- Lógica de integração do aplicativo. Isso inclui um canal de mensagens, principalmente com base em agentes de mensagens.

O aplicativo exigirá alta escalabilidade, permitindo que seus subsistemas verticais escalem horizontalmente de forma autônoma, pois alguns subsistemas exigirão maior escalabilidade que outros.

O aplicativo deverá ter a possibilidade de ser implantado em ambientes de várias infraestruturas (várias nuvens públicas e localmente) e, idealmente, ser multiplataforma, podendo ser mudado facilmente do Linux para o Windows (ou vice-versa).

## <a name="development-team-context"></a>Contexto da equipe de desenvolvimento

Pressupõe-se também o seguinte sobre o processo de desenvolvimento do aplicativo:

- Você tem várias equipes de desenvolvimento com foco em diferentes áreas de negócios do aplicativo.

- Os novos membros da equipe devem se tornar produtivos rapidamente, e o aplicativo deve ser fácil de entender e modificar.

- O aplicativo terá uma evolução de longo prazo e regras de negócio em constante mudança.

- Você precisará de facilidade de manutenção a longo prazo, o significa a agilidade na implementação de novas alterações no futuro possibilitando a atualização de vários subsistemas com impacto mínimo nos outros subsistemas.

- Você deseja a prática de integração contínua e implantação contínua do aplicativo.

- Você deseja aproveitar as tecnologias emergentes (estruturas, linguagens de programação, etc.) durante a evolução do aplicativo. Você não quer fazer migrações completas do aplicativo ao mudar para novas tecnologias, pois isso resultaria em custos altos e afetaria a previsibilidade e a estabilidade do aplicativo.

## <a name="choosing-an-architecture"></a>Escolhendo uma arquitetura

Qual deve ser a arquitetura de implantação do aplicativo? As especificações do aplicativo, junto com o contexto de desenvolvimento, sugerem enfaticamente que você deve projetar o aplicativo decompondo-o em subsistemas autônomos, na forma de microsserviços e contêineres de colaboração, em que um microsserviço é um contêiner.

Nessa abordagem, cada serviço (contêiner) implementa um conjunto de funções coesas e estritamente relacionadas. Por exemplo, um aplicativo pode consistir em serviços como: serviço de catálogo, serviço de pedidos, serviço de carrinho de compras, serviço de perfil do usuário, etc.

Os microsserviços se comunicam usando protocolos como HTTP (REST), mas também de forma assíncrona (usando AMQP, por exemplo) sempre que possível, especialmente ao propagar atualizações com eventos de integração.

Os microsserviços são desenvolvidos e implantados como contêineres independentes uns dos outros. Isso significa que uma equipe de desenvolvimento pode desenvolver e implantar um determinado microsserviço sem afetar outros subsistemas.

Cada microsserviço tem seu próprio banco de dados, permitindo que ele seja totalmente separado dos outros microsserviços. Quando necessário, a consistência entre bancos de dados de diferentes microsserviços é obtida com o uso de eventos de integração no nível do aplicativo (por meio de um barramento de eventos lógico), conforme manipulados na CQRS (segregação de responsabilidade de comando e consulta). Por isso, as restrições de negócios devem adotar consistência eventual entre os vários microsserviços e bancos de dados relacionados.

### <a name="eshoponcontainers-a-reference-application-for-net-core-and-microservices-deployed-using-containers"></a>eShopOnContainers: um aplicativo de referência para .NET Core e microsserviços implantados com o uso de contêineres

Para que você possa se concentrar na arquitetura e nas tecnologias em vez de pensar em um domínio corporativo hipotético desconhecido, selecionamos um domínio corporativo bem conhecido, ou seja, um aplicativo simplificado de comércio eletrônico (loja eletrônica) que apresenta um catálogo de produtos, recebe pedidos de clientes, verifica o estoque e executa outras funções de negócios. O código-fonte desse aplicativo baseado em contêineres está disponível no repositório [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) do GitHub.

O aplicativo consiste em vários subsistemas, incluindo vários front-ends de interface do usuário da loja (um aplicativo Web e um aplicativo móvel nativo), juntamente com os microsserviços e contêineres de back-end para todas as operações necessárias do lado do servidor com vários Gateways de API como pontos de entrada consolidados para os microsserviços internos. A figura 6-1 mostra a arquitetura do aplicativo de referência.

![Os clientes móveis e SPA se comunicam com pontos de entrada de gateway de API únicos, que então se comunicam com os microsserviços. Os clientes da Web tradicionais se comunicam com o microsserviço MVC, que se comunica com microsserviços](./media/image1.png)

**Figura 6-1**. A arquitetura do aplicativo de referência eShopOnContainers para o ambiente de desenvolvimento

**Ambiente de hospedagem**. Na Figura 6-1, você vê vários contêineres implantados em um único host do Docker. Esse seria o caso ao implantar em um único host do Docker com o comando docker-compose up. No entanto, se você estiver usar um orquestrador ou cluster de contêineres, cada contêiner poderá ser executado em um host (nó) diferente, e qualquer nó poderá ser executado em qualquer número de contêineres, como explicado anteriormente na seção sobre arquitetura.

**Arquitetura de comunicação**. O aplicativo eShopOnContainers usa dois tipos de comunicação, dependendo do tipo de ação funcional (consultas versus atualizações e transações):

- Comunicação entre cliente HTTP e microsserviço por meio de gateways de API. Isso é usado para consultas e ao aceitar comandos transacionais ou de atualização dos aplicativos cliente. A abordagem usando gateways de API é explicada em detalhes nas seções posteriores.

- Comunicação baseada em evento assíncrono. Isso ocorre por meio de um barramento de eventos para propagar atualizações em microsserviços ou integrar com aplicativos externos. O barramento de eventos pode ser implementado com qualquer tecnologia de infraestrutura de agente de mensagens, como RabbitMQ, ou usando barramentos de serviços de nível mais alto (nível de abstração), como Barramento de Serviço do Azure, NServiceBus, MassTransit ou Brighter.

O aplicativo é implantado como um conjunto de microsserviços na forma de contêineres. Aplicativos cliente podem se comunicar com esses microsserviços em execução como contêineres por meio de URLs públicas publicadas pelos gateways de API.

### <a name="data-sovereignty-per-microservice"></a>Soberania de dados por microsserviço

No aplicativo de exemplo, cada microsserviço tem seu próprio banco de dados ou fonte de dados, embora todos os bancos de dados do SQL Server sejam implantados em um único contêiner. Essa decisão de design foi tomada apenas para facilitar para um desenvolvedor ao obter o código do GitHub, cloná-lo e abri-lo no Visual Studio ou o Visual Studio Code. Como alternativa, ela facilita para compilar as imagens personalizadas do Docker usando a CLI do .NET Core e a CLI do Docker e, em seguida, facilita para implantá-las e executá-las em um ambiente de desenvolvimento do Docker. De uma forma ou de outra, o uso de contêineres para fontes de dados permite que os desenvolvedores criem e implantem em questão de minutos, sem a necessidade de provisionar um banco de dados externo ou qualquer outra fonte de dados com dependências rígidas na infraestrutura (de nuvem ou local).

Em um ambiente de produção real, por questões de alta disponibilidade e escalabilidade, os bancos de dados devem ser baseados em servidores de banco de dados na nuvem ou locais, mas não em contêineres.

Portanto, as unidades de implantação para os microsserviços (e até mesmo para bancos de dados deste aplicativo) são contêineres do Docker e o aplicativo de referência é um aplicativo de vários contêineres que adota princípios de microsserviços.

### <a name="additional-resources"></a>Recursos adicionais

- **repositório GitHub do eShopOnContainers. Código-fonte do aplicativo de referência**  
    [https://aka.ms/eShopOnContainers/](https://aka.ms/eShopOnContainers/)

## <a name="benefits-of-a-microservice-based-solution"></a>Benefícios de uma solução baseada em microsserviços

Uma solução de baseada em microsserviços tem muitos benefícios:

**Cada microsserviço é relativamente pequeno, fácil de gerenciar e desenvolver**. Especificamente:

- É fácil para um desenvolvedor entender e se familiarizar rapidamente com boa produtividade.

- Os contêineres são rapidamente iniciados, tornando os desenvolvedores mais produtivos.

- Um IDE como Visual Studio pode carregar projetos menores rapidamente, fazendo com que os desenvolvedores sejam mais produtivos.

- Cada microsserviço pode ser criado, desenvolvido e implantado independentemente de outros microsserviços. Isso proporciona agilidade, porque é mais fácil implantar novas versões dos microsserviços com frequência.

**É possível escalar horizontalmente áreas individuais do aplicativo**. Por exemplo, suponha que o serviço de catálogo ou do carrinho de compras tenha que ser expandido, mas não o processo de pedidos. Uma infraestrutura de microsserviços será muito mais eficiente do que uma arquitetura monolítica em relação aos recursos usados ao expandir.

**Você pode dividir o trabalho de desenvolvimento entre várias equipes**. Cada serviço pode ser de propriedade de única uma equipe de desenvolvimento. Cada equipe pode gerenciar, desenvolver, implantar e dimensionar o serviço de maneira independente das outras equipes.

**Os problemas são mais isolados**. Se houver um problema em um serviço, somente esse serviço será inicialmente afetado (exceto quando um design incorreto for usado, com dependências diretas entre microsserviços) e os outros serviços poderão continuar lidando com as solicitações. Por outro lado, um componente com defeito em uma arquitetura de implantação monolítica poderá derrubar todo o sistema, especialmente quando envolver recursos, como uma perda de memória. Além disso, quando um problema em um microsserviço for resolvido, você poderá implantar apenas o microsserviço afetado sem afetar o restante do aplicativo.

**Você pode usar as tecnologias mais recentes**. Com a possibilidade de começar a desenvolver serviços de forma independente e executá-los lado a lado (graças aos contêineres e ao .NET Core), você pode usar as últimas tecnologias e estruturas de acordo com a conveniência, em vez de ficar preso a uma pilha ou estrutura mais antiga para todo o aplicativo.

## <a name="downsides-of-a-microservice-based-solution"></a>Desvantagens de uma solução baseada em microsserviços

Uma solução com base em microsserviços como essa também apresenta algumas desvantagens:

**Aplicativo distribuído**. A distribuição do aplicativo cria complexidades para os desenvolvedores ao projetar e criar os serviços. Por exemplo, os desenvolvedores devem implementar comunicação entre serviços usando protocolos como HTTP ou AMPQ, o que adiciona complexidade para os testes e o tratamento de exceções. Isso também adiciona latência ao sistema.

**Complexidade de implantação**. Um aplicativo com vários tipos de microsserviços e que necessite de alta escalabilidade (ele precisa ser capaz de criar várias instâncias por serviço e equilibrar os serviços em vários hosts) gera um alto grau de complexidade de implantação para o gerenciamento e as operações de TI. Se você não estiver usando uma infraestrutura orientada a microsserviços (como um agendador e orquestrador), essa complexidade adicional poderá exigir esforços de desenvolvimento muito maiores que o próprio aplicativo de negócios.

**Transações atômicas**. Geralmente, as transações atômicas entre vários microsserviços não são possíveis. Os requisitos corporativos precisam adotar a consistência eventual entre vários microsserviços.

**Maiores necessidades de recursos globais** (memória total, unidades e recursos de rede para todos os servidores ou hosts). Em muitos casos, ao substituir um aplicativo monolítico por uma abordagem de microsserviços, a quantidade de recursos globais iniciais necessários para o novo aplicativo baseado em microsserviços será maior do que as necessidades de infraestrutura do aplicativo monolítico original. Isso ocorre porque o maior grau de granularidade e serviços distribuídos exige mais recursos globais. No entanto, considerando o baixo custo de recursos em geral e o benefício de expandir apenas determinadas áreas do aplicativo, comparados aos custos de longo prazo relacionados aos desenvolvimento de aplicativos monolíticos, o aumento no uso de recursos geralmente compensa nas grandes aplicações de longo prazo.

**Problemas com a comunicação direta entre cliente e microsserviço**. Se o aplicativo for grande, com dezenas de microsserviços, haverá desafios e limitações se houver necessidade de comunicações diretas entre o cliente e o microsserviço. Um problema é uma potencial incompatibilidade entre as necessidades do cliente e as APIs expostas por cada um dos microsserviços. Em alguns casos, o aplicativo cliente precisará fazer muitas solicitações separadas para compor a interface do usuário, tornando-se ineficiente na Internet e impraticável em uma rede móvel. Portanto, as solicitações do aplicativo cliente ao sistema de back-end devem ser minimizadas.

Outro problema com a comunicação direta entre cliente e microsserviço é que alguns microsserviços podem usar protocolos que não sejam compatíveis com a Web. Um serviço pode usar um protocolo binário, enquanto outro pode usar o sistema de mensagens AMQP. Esses protocolos não são compatíveis com firewalls e são mais bem usados internamente. Normalmente, um aplicativo deve usar protocolos como HTTP e WebSockets para a comunicação do lado de fora do firewall.

Outra desvantagem dessa abordagem direta entre cliente e serviço é que ela dificulta a refatoração dos contratos desses microsserviços. Ao longo do tempo, talvez os desenvolvedores queiram alterar a forma como o sistema está particionado em serviços. Por exemplo, eles podem mesclar dois serviços ou dividir um serviço em dois ou mais serviços. No entanto, se os clientes se comunicarem diretamente com os serviços, esse tipo de refatoração poderá interromper a compatibilidade com aplicativos cliente.

Conforme mencionado na seção de arquitetura, ao projetar e criar um aplicativo complexo baseado em microsserviços, considere o uso de vários Gateways de API refinados em vez da abordagem mais simples de comunicação direta entre cliente e microsserviço.

**Particionamento dos microsserviços**. Por fim, independentemente da abordagem escolhida para sua arquitetura de microsserviços, outro desafio é decidir como particionar um aplicativo de ponta a ponta em vários microsserviços. Conforme observado na seção de arquitetura do guia, há várias técnicas e abordagens que você pode escolher. Basicamente, você precisa identificar áreas do aplicativo que sejam separados de outras áreas e que tenham um número baixo de dependências rígidas. Em muitos casos, isso se alinha ao particionamento de serviços de acordo com o caso de uso. Por exemplo, em nosso aplicativo de loja eletrônica, temos um serviço de pedidos que é responsável por toda a lógica de negócios relacionada ao processo de pedido. Também temos o serviço de catálogo e o serviço de carrinho de compras, que implementam outros recursos. Idealmente, cada serviço deveria ter somente um pequeno conjunto de responsabilidades. Isso é semelhante ao princípio SRP (princípio de responsabilidade única) aplicado a classes, que declara que uma classe deve ter somente uma razão para ser alterada. Mas, nesse caso, estamos lidando com microsserviços, portanto o escopo será maior que o de uma única classe. Acima de tudo, um microsserviço deve ser completamente autônomo, de ponta a ponta, incluindo a responsabilidade por suas próprias fontes de dados.

## <a name="external-versus-internal-architecture-and-design-patterns"></a>Padrões de arquitetura e design externos versus internos

A arquitetura externa é a arquitetura de microsserviço composta por vários serviços, de acordo com os princípios descritos na seção de arquitetura deste guia. No entanto, dependendo da natureza de cada microsserviço e, independentemente da arquitetura de microsserviço de alto nível que você escolhe, é comum e muitas vezes aconselhável, ter arquiteturas internas distintas para os diferentes microsserviços, cada qual baseada em padrões diferentes. Os microsserviços podem até usar tecnologias e linguagens de programação diferentes. A figura 6-2 ilustra essa diversidade.

![Diferença entre arquitetura externa: padrões de microsserviço, gateways de API, comunicação resilientes, pub/sub etc. e a arquitetura interna: controlado por dados/CRUD, padrões de DDD, injeção de dependência, várias bibliotecas etc.](./media/image2.png)

**Figura 6-2**. Arquitetura e design externos versus internos

Por exemplo, em nosso *eShopOnContainers* de exemplo, os microsserviços de catálogo, carrinho de compras e de perfil do usuário são simples (basicamente, subsistemas CRUD). Portanto, a arquitetura interna e o design deles são bastante simples. No entanto, você pode ter outros microsserviços, como o microsserviço de pedidos, que é mais complexo e representa regras de negócios em constante mudança, com um alto grau de complexidade de domínio. Nesses casos, pode ser interessante implementar padrões mais avançados em um microsserviço específico, como aqueles definidos nas abordagens de DDD (design controlado por domínio), como estamos fazendo no microsserviço de pedidos do *eShopOnContainers*. (Examinaremos esses padrões de DDD em uma seção posterior que explica a implementação do microsserviço de pedidos do *eShopOnContainers*).

Outro motivo para uma tecnologia diferente para cada microsserviço seria a natureza de cada microsserviço. Por exemplo, talvez seja melhor usar uma linguagem de programação funcional, como F\#, ou uma linguagem como a R, se você estiver destinando a domínios de aprendizado de máquina e inteligência artificial, em vez de uma linguagem de programação mais orientada a objeto, como a C\#.

O resultado é que cada microsserviço pode ter uma arquitetura interna diferente com base nos diferentes padrões de design. Nem todos os microsserviços devem ser implementados usando padrões avançados de DDD, porque que isso seria excesso de engenharia. Da mesma forma, microsserviços complexos, com lógica de negócios em constante mudança, não devem ser implementados como componentes de CRUD, ou você poderá ficar com um código de baixa qualidade. 

## <a name="the-new-world-multiple-architectural-patterns-and-polyglot-microservices"></a>O novo mundo: vários padrões de arquitetura e microsserviços poliglotas

Há muitos padrões de arquitetura usados por desenvolvedores e arquitetos de software. Veja alguns a seguir (combinando estilos de arquitetura e padrões de arquitetura):

- CRUD simples, de camada e nível únicos.

- [Tradicional em N camadas](https://msdn.microsoft.com/library/ee658109.aspx#Layers).

- [Design controlado po domínio em N camadas](https://blogs.msdn.microsoft.com/cesardelatorre/2011/07/03/published-first-alpha-version-of-domain-oriented-n-layered-architecture-v2-0/).

- [Arquitetura limpa](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html) (com a usada no [eShopOnWeb](https://aka.ms/WebAppArchitecture))

- [CQRS](https://martinfowler.com/bliki/CQRS.html) (Segregação de Responsabilidade de Comando e Consulta).

- [EDA](https://en.wikipedia.org/wiki/Event-driven_architecture) (Arquitetura controlada por eventos).

Você também pode criar microsserviços com várias tecnologias e linguagens, como APIs Web do ASP.NET Core, NancyFx, SignalR do ASP.NET Core (disponível no .NET Core 2), F\#, Node.js, Python, Java, C++, GoLang e muito mais.

O ponto importante é que não há um padrão de arquitetura ou estilo específico nem qualquer tecnologia em particular que seja ideal para todas as situações. A figura 6-3 mostra algumas abordagens e tecnologias (embora não estejam em nenhuma ordem específica) que podem ser usadas em microsserviços diferentes.

![Os microsserviços poliglotas e de padrão de várias arquiteturas significam que você pode combinar linguagens e tecnologias com as necessidades de cada microsserviço e ainda fazer com que eles conversem entre si.](./media/image3.png)

**Figura 6-3**. Padrões de várias arquitetura e o mundo de microsserviços poliglotas

Conforme mostrado na Figura 6-3, em aplicativos compostos de muitos microsserviços (de contextos delimitados, na terminologia de design controlado por domínio ou simplesmente "subsistemas", como microsserviços autônomos), você pode implementar cada microsserviço de maneira diferente. Cada um pode ter um padrão de arquitetura diferente e usar linguagens e bancos de dados diferentes, dependendo da natureza, dos requisitos empresariais e das prioridades do aplicativo. Em alguns casos, o microsserviços podem ser semelhantes. Mas, geralmente, esse não é o caso, porque o limite de contexto e os requisitos de cada subsistema costumam ser diferentes.

Por exemplo, em um aplicativo CRUD simples de manutenção, não faz sentido projetar e implementar padrões de DDD. Mas, para seu negócio principal ou domínio principal, é interessante aplicar padrões mais avançados para lidar com a complexidade dos negócios e com as regras de negócio em constante mudança.

Especialmente ao lidar com grandes aplicativos compostos por vários subsistemas, você não deve aplicar uma única arquitetura de alto nível com base em um único padrão de arquitetura. Por exemplo, a CQRS não deve ser aplicada como uma arquitetura de alto nível para um aplicativo inteiro, mas pode ser útil para um conjunto específico de serviços.

Não há solução definitiva nem um padrão de arquitetura correto para cada caso específico. Você não pode ter "um padrão de arquitetura para controlar tudo". Dependendo das prioridades de cada microsserviço, você deverá escolher uma abordagem diferente para cada um deles, conforme explicado nas seções a seguir.

>[!div class="step-by-step"]
>[Anterior](index.md)
>[Próximo](data-driven-crud-microservice.md)