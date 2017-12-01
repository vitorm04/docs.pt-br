---
title: "Criar um microsserviço orientado DDD"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Criar um microsserviço orientado DDD"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: df45441089fd59d5e0e52b4bcec409adcc11fb71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="designing-a-ddd-oriented-microservice"></a>Criar um microsserviço orientado DDD

Design orientado a domínio (DDD) advogados modelagem com base em realidade dos negócios como relevantes para seus casos de uso. No contexto da criação de aplicativos, DDD fala sobre problemas de domínios. Ele descreve as áreas de problema independente como contextos limitada (cada contexto limitado se correlaciona com um microsserviço) e enfatizar uma linguagem comum para falar sobre esses problemas. Também sugere muitos conceitos técnicos e padrões, como entidades de domínio com modelos avançados (nenhum [modelo de domínio anêmica](https://martinfowler.com/bliki/AnemicDomainModel.html)), regras de valor objetos, agregações e raiz de agregação (ou entidade raiz) para dar suporte à implementação interna. Esta seção apresenta o design e a implementação desses padrões internos.

Às vezes, esses padrões e regras de técnicas de DDD são consideradas obstáculos que têm uma curva de aprendizado acentuada para implementar DDD abordagens. Mas a parte importante é não os padrões, mas organizar o código para que ele será alinhado para os problemas de negócios e usando os mesmos termos de negócios (onipresente language). Além disso, as abordagens DDD devem ser aplicadas somente se você estiver implementando microservices complexas com regras de negócio significativas. Responsabilidades mais simples, como um serviço CRUD, podem ser gerenciadas com abordagens mais simples.

Onde desenhar os limites é a chave ao criar e definir um microsserviço. Padrões DDD ajudam a compreender a complexidade do domínio. Para o modelo de domínio para cada contexto limitado, você pode identificar e define agregações que seu domínio de modelo, entidades e objetos de valor. Criar e refinar um modelo de domínio que está contido dentro de um limite que define o contexto. E isso é bastante explícito na forma de um microsserviço. Os componentes dentro desses limites acabam sendo sua microservices, embora em alguns casos, uma continuidade de negócios ou microservices de negócios pode ser composto de vários serviços físicos. DDD é sobre limites e então são microservices.

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a>Manter o microsserviço limites de contexto relativamente pequeno

Determinar onde colocar os limites entre contextos limitada equilibra a dois objetivos concorrentes. Primeiro, você deseja criar inicialmente o menor possível microservices, embora isso não deve ser o principal driver; Você deve criar um limite de itens que precisam coesão. Em seguida, você deseja evitar a comunicação verborrágica entre microservices. Essas metas podem entrar em uma da outra. Você deve equilibrá-los por Decomposição do sistema em quantos microservices pequenos pode até que você veja os limites da comunicação crescendo rapidamente com cada tentativa adicional para separar um novo contexto associado. Coesão é a chave em um único contexto associado.

É semelhante do [cheiro de código intimidade inadequada](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) durante a implementação de classes. Se dois microservices precisam colaborar muito entre si, eles devem ser provavelmente o mesmo microsserviço.

Outra forma de encarar isso é autonomia. Se um microsserviço deve confiar em outro serviço para uma solicitação de serviço diretamente, não é realmente autônomo.

## <a name="layers-in-ddd-microservices"></a>Camadas no DDD microservices

A maioria dos aplicativos empresariais com significativos para os negócios e a complexidade técnica são definidos por várias camadas. As camadas são um artefato lógico e não estão relacionadas à implantação do serviço. Elas existem para ajudar os desenvolvedores a gerenciar a complexidade no código. Camadas diferentes (como a camada de modelo de domínio versus a camada de apresentação, etc.) podem ter tipos diferentes, que exige conversões entre esses tipos.

Por exemplo, uma entidade pode ser carregada do banco de dados. Em seguida, parte de informações ou uma agregação de informações, incluindo dados adicionais de outras entidades, pode ser enviado para o cliente da interface do usuário por meio de uma API da Web REST. O ponto aqui é que a entidade de domínio está contida na camada de modelo de domínio e não deve ser propagada para outras áreas que ele não pertence, como para a camada de apresentação.

Além disso, você precisa ter entidades sempre válido (consulte a [criar validações na camada de modelo de domínio](#designing-validations-in-the-domain-model-layer) seção) controlado pelo raízes agregadas (entidades de raiz). Portanto, entidades não devem ser associadas aos modos de exibição do cliente, porque o nível de interface do usuário alguns dados podem não ser validados. Isso é o que é o ViewModel para. O ViewModel é um modelo de dados exclusivamente para necessidades de camada de apresentação. As entidades de domínio não pertencem diretamente ao ViewModel. Em vez disso, você precisa converter entre entidades ViewModels e domínio e vice-versa.

Quando lidando com complexidade, é importante ter um modelo de domínio controlado pelo raízes agregadas (entrarmos em isso em mais detalhes posteriormente) Certifique-se de que todas as constantes e regras relacionam a esse grupo de entidades (agregação) são executadas por meio de uma única entrada ponto de saída ou entrada, a raiz de agregação.

Figura 9-5 mostra como um design em camadas é implementado no aplicativo eShopOnContainers.

![](./media/image6.png)

**Figura 9-5**. Camadas DDD a ordenação microsserviço em eShopOnContainers

Você deseja criar o sistema de forma que cada camada se comunica apenas com determinados outras camadas. Que pode ser mais fácil para impor se camadas são implementadas como bibliotecas de classes diferentes, porque você pode identificar claramente que dependências são definidas entre bibliotecas. Por exemplo, a camada de modelo de domínio não deve receber uma dependência em qualquer outra camada (as classes de modelo de domínio devem ser Plain Old CLR Objects, ou [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object), classes). Conforme mostrado na Figura 9-6, o **Ordering.Domain** biblioteca camada tem dependências somente em bibliotecas do .NET Core, mas não em qualquer outra biblioteca personalizada de (biblioteca de dados, a biblioteca de persistência, etc.).

![](./media/image7.PNG)

**Figura 9-6**. Implementado conforme bibliotecas permitem melhor controle de dependências entre as camadas de camadas

### <a name="the-domain-model-layer"></a>A camada de modelo de domínio

Catálogo excelente de Eric Evans [Design controlado por domínio](http://domainlanguage.com/ddd/) diz o seguinte sobre a camada de modelo de domínio e a camada de aplicativo.

**Camada de modelo de domínio**: responsável para representar conceitos de negócios, informações sobre a situação de negócios e as regras de negócio. Estado que reflete a situação de negócios é controlado e usado aqui, embora os detalhes técnicos de fazê-lo são delegados para a infraestrutura. Essa camada é a essência do software de negócios.

A camada de modelo de domínio é onde os negócios é expresso. Quando você implementa uma camada de modelo de domínio de microsserviço no .NET, a camada é codificada como uma biblioteca de classes com as entidades de domínio que capturam dados mais comportamento (métodos com lógica).

Seguindo o [ignorância de persistência](http://deviq.com/persistence-ignorance/) e [infraestrutura ignorância](https://ayende.com/blog/3137/infrastructure-ignorance) princípios, essa camada completamente devem ignorar os detalhes de persistência de dados. Essas tarefas de persistência devem ser executadas pela camada de infraestrutura. Portanto, essa camada não deveria receber dependências diretas na infraestrutura, o que significa que uma regra importante é que suas classes de entidade do modelo de domínio devem ser [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)s.

Entidades de domínio não devem ter nenhuma dependência direta (como derivando uma classe base) em qualquer estrutura de infraestrutura de acesso de dados como o Entity Framework ou NHibernate. Idealmente, suas entidades de domínio não devem derivar de ou implementar qualquer tipo definido em qualquer estrutura de infraestrutura.

Mais modernas estruturas ORM como Entity Framework Core permitem essa abordagem, de modo que suas classes de modelo de domínio não estão ligadas à infraestrutura. No entanto, com as entidades POCO nem sempre é possível ao usar determinados bancos de dados NoSQL e estruturas, como atores e coleções confiável no Azure Service Fabric.

Mesmo quando é importante seguir o princípio de ignorância de persistência para o modelo de domínio, você não deve ignorar preocupações de persistência. Ainda é muito importante entender o modelo de dados físicos e como ele mapeia para o modelo de objeto de entidade. Caso contrário, você pode criar designs impossíveis.

Além disso, isso não significa que pode levar a um modelo criado para um banco de dados relacional e diretamente movê-lo para um banco de dados orientado por documentos ou o NoSQL. Em alguns modelos de entidade, poderá ajustar o modelo, mas geralmente não. Ainda há restrições que o modelo de entidade deve cumprir, baseadas na tecnologia de armazenamento e tecnologia ORM.

### <a name="the-application-layer"></a>A camada de aplicativo

Passar para a camada de aplicativo, estamos novamente pode citar o catálogo de Eric Evans [Design controlado por domínio](http://domainlanguage.com/ddd/):

**Camada de aplicativo:** define os trabalhos que o software deve para fazer e direciona os objetos de domínio expressivas para resolver problemas. As tarefas por que nesta camada é responsável são significativos para os negócios ou necessárias para a interação com as camadas do aplicativo de outros sistemas. Essa camada é mantida dinâmico. Ele não contém regras de negócio ou dados de Conhecimento, mas apenas tarefas de coordenadas e delegados funcionam para colaborações de objetos de domínio na próxima camada para baixo. Ele não tem estado refletir a situação de negócios, mas pode ter um estado que reflete o progresso de uma tarefa para o usuário ou o programa.

Normalmente, a camada de aplicativo do microsserviço no .NET é codificada como um projeto de API da Web do ASP.NET Core. O projeto implementa interação do microsserviço, acesso remoto à rede e as APIs da Web externo usado nos aplicativos de interface do usuário ou cliente. Ele inclui consultas se aproximar usando um CQRS, comandos aceitos pelo microsserviço e até mesmo a comunicação controlada por evento entre microservices (eventos de integração). A API Web do ASP.NET Core que representa a camada de aplicativo não deve conter as regras de negócio ou conhecimento do domínio (especialmente regras de domínio para transações ou atualizações); eles devem ser de propriedade pela biblioteca de classe de modelo de domínio. A coordenada do aplicativo camada deve apenas tarefas e não deve conter ou definir qualquer estado de domínio (modelo de domínio). Ela delega a execução de regras de negócio para as domínio modelo próprias classes (raízes agregadas e entidades de domínio), que, por fim, atualizará os dados dentro dessas entidades de domínio.

Basicamente, a lógica do aplicativo é onde você pode implementar todos os casos de uso que dependem de um determinado front-end. Por exemplo, a implementação relacionada a um serviço de API da Web.

O objetivo é que a lógica do domínio na camada de modelo de domínio, seus invariáveis, o modelo de dados e regras de negócio relacionadas deve ser completamente independente entre as camadas de apresentação e de aplicativo. Mais de tudo, a camada de modelo de domínio deve não depende diretamente qualquer estrutura de infraestrutura.

### <a name="the-infrastructure-layer"></a>A camada de infraestrutura

A camada de infraestrutura é como os dados que inicialmente são mantidos em entidades de domínio (em memória) são mantidos em bancos de dados ou outro repositório persistente. Um exemplo é usar o código do Entity Framework Core para implementar as classes de padrão de repositório que usa um DBContext para manter dados em um banco de dados relacional.

Conforme mencionado anteriormente [ignorância de persistência](http://deviq.com/persistence-ignorance/) e [infraestrutura ignorância](https://ayende.com/blog/3137/infrastructure-ignorance) princípios, a camada de infraestrutura devem não "contaminarem" a camada de modelo de domínio. Você deve manter o independente de classes de entidade do domínio modelo da infraestrutura de que você usa para manter dados (EF ou qualquer outra estrutura) não Obtendo dependências de disco rígidas em estruturas. A biblioteca de classes de camada de modelo de domínio deve ter somente o código de domínio, apenas [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) entidade classes Implementando a essência do seu software e completamente separada de tecnologias de infraestrutura.

Assim, suas camadas ou bibliotecas de classes e projetos, por fim, depende de sua camada de modelo de domínio (biblioteca), não vice-versa, conforme mostrado na Figura 9-7.

![](./media/image8.png)

**Figura 9-7**. Dependências entre camadas em DDD

Esse design de camada deve ser independente para cada microsserviço. Conforme observado anteriormente, você pode implementar o microservices mais complexo (CRUD simple em uma única camada) microservices seguintes padrões DDD, durante a implementação mais simples controlada por dados de forma mais simples.

#### <a name="additional-resources"></a>Recursos adicionais

-   **DevIQ. Princípio de ignorância de persistência**
    [*http://deviq.com/persistence-ignorance/*](http://deviq.com/persistence-ignorance/)

-   **Oren Eini. Infraestrutura ignorância**
    [*https://ayende.com/blog/3137/infrastructure-ignorance*](https://ayende.com/blog/3137/infrastructure-ignorance)

-   **Anjo Lopez. Em camadas de arquitetura no Design controlado por domínio**
    [*https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/*](https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/)


>[!div class="step-by-step"]
[Anterior] (cqrs-microsserviço-reads.md) [Avançar] (microsserviço-domínio-model.md)
