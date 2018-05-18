---
title: Projetando um microsserviço orientado a DDD
description: Arquitetura de microsserviços .NET para aplicativos .NET em contêineres | Criar um microsserviço orientado a DDD
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/06/2017
ms.openlocfilehash: 520f2928eb0d300ab0dc2d328d974455e102e4d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="designing-a-ddd-oriented-microservice"></a>Projetando um microsserviço orientado a DDD

O DDD (design orientado a domínio) defende modelagem com base na realidade dos negócios conforme relevante para os seus casos de uso. No contexto da criação de aplicativos, o DDD fala sobre problemas como domínios. Ele descreve as áreas de problema independentes como Contextos Limitados (cada Contexto Limitado se correlaciona a um microsserviço) e enfatiza uma linguagem comum para falar sobre esses problemas. Também sugere muitos conceitos técnicos e padrões, como entidades de domínio com regras de modelos avançados (nenhum [modelo de domínio anêmico](https://martinfowler.com/bliki/AnemicDomainModel.html)), objetos de valor, agregações e raiz de agregação (ou entidade raiz) para dar suporte à implementação interna. Esta seção apresenta o design e a implementação desses padrões internos.

Às vezes, esses padrões e regras técnicas de DDD são considerados obstáculos que têm uma curva de aprendizado acentuada para implementar abordagens de DDD. Mas a parte importante não são os padrões em si, mas organizar o código para que ele fique alinhado aos problemas de negócios e usar os mesmos termos de negócios (linguagem ubíqua). Além disso, as abordagens DDD deverão ser aplicadas somente se você estiver implementando microsserviços complexos com regras de negócio significativas. Responsabilidades mais simples, como um serviço CRUD, podem ser gerenciadas com abordagens mais simples.

Onde traçar os limites é a tarefa principal ao criar e definir um microsserviço. Padrões DDD ajudam você a compreender a complexidade no domínio. Para o modelo de domínio para cada Contexto Limitado, você pode identificar e definir as entidades, os objetos de valor e agregações que modelem seu domínio. Você cria e refina um modelo de domínio contido dentro de um limite que define o seu contexto. E isso é bastante explícito na forma de um microsserviço. Os componentes dentro desses limites acabam sendo seus microsserviços, embora, em alguns casos, uma continuidade de negócios ou microsserviços de negócios possam ser compostos por vários serviços físicos. DDD é sobre limites, assim como os microsserviços.

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a>Mantenha os limites de contexto do microsserviço relativamente pequenos

Determinar onde colocar os limites entre Contextos Limitados equilibra dois objetivos concorrentes. Primeiro, você deseja criar inicialmente os menores microsserviços possíveis, embora isso não deva ser a meta principal; você deve criar um limite em torno de itens que precisam de coesão. Segundo, você deseja evitar comunicações verborrágica entre microsserviços. Essas metas podem contradizer umas às outras. Você deve equilibrá-las decompondo o sistema em tantos microsserviços quanto puder até ver esses limites de comunicação crescendo rapidamente a cada tentativa adicional de separar um novo contexto limitado. Coesão é essencial em um único contexto limitado.

É semelhante ao [cheiro de código de Intimidade Inadequada](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) ao implementar classes. Se dois microsserviços precisarem colaborar muito entre si, eles deverão provavelmente ser o mesmo microsserviço.

Outra forma de encarar isso é autonomia. Se um microsserviço precisar confiar em outro serviço para atender diretamente a uma solicitação, ele não será realmente autônomo.

## <a name="layers-in-ddd-microservices"></a>Camadas em microsserviços de DDD

A maioria dos aplicativos empresariais com complexidade de negócios e técnica significativa é definida por várias camadas. As camadas são um artefato lógico e não estão relacionadas à implantação do serviço. Elas existem para ajudar os desenvolvedores a gerenciar a complexidade no código. Camadas diferentes (como a camada de modelo de domínio versus a camada de apresentação etc.) podem ter tipos diferentes, o que exige conversões entre esses tipos.

Por exemplo, uma entidade pode ser carregada do banco de dados. Em seguida, parte dessas informações ou uma agregação de informações, incluindo dados adicionais de outras entidades, podem ser enviadas para uma interface do usuário do cliente por meio de uma API da Web REST. O ponto aqui é que a entidade de domínio está contida na camada de modelo de domínio e não deve ser propagada para outras áreas às quais ela não pertence, como a camada de apresentação.

Além disso, você precisa ter entidades sempre válidas (consulte a seção [Criar validações na camada de modelo de domínio](#designing-validations-in-the-domain-model-layer)) controlada por raízes agregadas (entidades raiz). Portanto, as entidades não devem ser associadas aos modos de exibição do cliente pois, no nível da interface do usuário, alguns dados podem ainda não ter sido validados. É para isso que serve o ViewModel. O ViewModel é um modelo de dados exclusivamente para necessidades de camada de apresentação. As entidades de domínio não pertencem diretamente ao ViewModel. Em vez disso, você precisa converter entre entidades de domínio e ViewModels e vice-versa.

Ao lidar com complexidade, é importante ter um modelo de domínio controlado por raízes agregadas que garantam que todas as invariáveis e regras relacionadas àquele grupo de entidades (agregação) sejam executadas por meio de um único ponto de entrada ou porta, a raiz de agregação.

A Figura 9-5 mostra como um design em camadas é implementado no aplicativo eShopOnContainers.

![](./media/image6.png)

**Figura 9-5**. Camadas DDD no microsserviço de ordenação em eShopOnContainers

Você deseja criar o sistema de modo que cada camada se comunique apenas com determinadas outras camadas. Isso poderá ser mais fácil de impor se as camadas forem implementadas como bibliotecas de classes diferentes, porque você pode identificar claramente que dependências são definidas entre bibliotecas. Por exemplo, a camada de modelo de domínio não deve receber uma dependência de nenhuma outra camada (as classes de modelo de domínio devem ser [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) ou Plain Old CLR Objects). Conforme mostrado na Figura 9-6, a biblioteca de camada **Ordering.Domain** tem dependências apenas de bibliotecas .NET Core ou pacotes NuGet, mas não de nenhuma outra biblioteca personalizada, como a biblioteca de dados ou a biblioteca de persistência.

![](./media/image7.PNG)

**Figura 9-6**. Camadas implementadas como bibliotecas permitem melhor controle de dependências entre as camadas

### <a name="the-domain-model-layer"></a>A camada de modelo de domínio

O excelente livro de Eric Evans, [Domain Driven Design](https://domainlanguage.com/ddd/) (Projeto Orientado a Domínio) diz o seguinte sobre a camada de modelo de domínio e a camada de aplicativo.

**Camada de modelo de domínio**: responsável por representar conceitos de negócios, informações sobre a situação de negócios e as regras de negócio. O estado que reflete a situação de negócios é controlado e usado aqui, embora os detalhes técnicos de armazená-lo sejam delegados à infraestrutura. Essa camada é a essência do software de negócios.

A camada de modelo de domínio é onde os negócios é expresso. Quando você implementa uma camada de modelo de domínio de microsserviço em .NET, essa camada é codificada como uma biblioteca de classes com as entidades de domínio que capturam dados mais comportamento (métodos com lógica).

Seguindo os princípios de [Ignorância da Persistência](http://deviq.com/persistence-ignorance/) e a [Ignorância da Infraestrutura](https://ayende.com/blog/3137/infrastructure-ignorance), essa camada deve ignorar totalmente os detalhes de persistência de dados. Essas tarefas de persistência devem ser executadas pela camada de infraestrutura. Portanto, essa camada não deveria receber dependências diretas da infraestrutura, o que significa que uma regra importante é que suas classes de entidade do modelo de domínio devem ser [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)s.

Entidades de domínio não devem ter nenhuma dependência direta (como derivar de uma classe base) em nenhuma estrutura de infraestrutura de acesso a dados, como Entity Framework ou NHibernate. Idealmente, suas entidades de domínio não devem derivar nem implementar nenhum tipo definido em nenhuma estrutura de infraestrutura.

As estruturas ORM mais modernas, como Entity Framework Core, permitem essa abordagem, de modo que suas classes de modelo de domínio não estejam ligadas à infraestrutura. No entanto, ter entidades POCO nem sempre é possível ao usar determinados bancos de dados NoSQL e estruturas, como Atores e Coleções Confiáveis no Azure Service Fabric.

Mesmo quando é importante seguir o princípio de Ignorância de Persistência para o modelo de Domínio, você não deve ignorar preocupações de persistência. Ainda é muito importante entender o modelo de dados físicos e como ele é mapeado para o modelo de objeto de entidade. Caso contrário, você pode criar designs impossíveis.

Além disso, isso não significa que você pode pegar um modelo criado para um banco de dados relacional e movê-lo diretamente para um banco de dados orientado por documentos ou NoSQL. Em alguns modelos de entidade, o modelo pode se ajustar, mas geralmente não se ajusta. Ainda há restrições que o modelo de entidade deve cumprir, com base tanto na tecnologia de armazenamento quanto na tecnologia ORM.

### <a name="the-application-layer"></a>A camada de aplicativo

Passando para a camada de aplicativo, novamente podemos citar o livro de Eric Evans [Domain Driven Design](https://domainlanguage.com/ddd/) (Projeto Orientado a Domínio):

**Camada de aplicativo:** define os trabalhos que o software deve fazer e direciona os objetos de domínio expressivos para resolver problemas. As tarefas pelas quais esta camada é responsável são significativas para os negócios ou necessárias para a interação com as camadas do aplicativo de outros sistemas. Essa camada é mantida fina. Ele não contém regras de negócio nem conhecimento, mas apenas coordena o trabalho de tarefas e delegados para colaborações de objetos de domínio na próxima camada abaixo. Ele não tem um estado refletindo a situação de negócios, mas pode ter um estado que reflita o progresso de uma tarefa para o usuário ou o programa.

Uma camada de aplicativo do microsserviço no .NET é codificada como um projeto de API da Web do ASP.NET Core. O projeto implementa interação do microsserviço, o acesso remoto à rede e as APIs da Web externas usadas nos aplicativos de interface do usuário ou cliente. Ele incluirá consultas se estiver usando uma abordagem CQRS, comandos aceitos pelo microsserviço e até mesmo a comunicação controlada por evento entre microsserviços (eventos de integração). A API Web do ASP.NET Core que representa a camada de aplicativo não deve conter as regras de negócio nem o conhecimento do domínio (especialmente regras de domínio para transações ou atualizações); isso deve ser de propriedade da biblioteca de classes de modelo de domínio. A camada do aplicativo deve apenas coordenar tarefas e não deve reter nem definir qualquer estado de domínio (modelo de domínio). Ela delega a execução de regras de negócio para as classes de modelo de domínio em si (raízes agregadas e entidades de domínio), que, por fim, atualizarão os dados dentro dessas entidades de domínio.

Basicamente, a “lógica de aplicativo” é onde você implementa todos os casos de uso que dependem de um determinado front-end. Por exemplo, a implementação relacionada a um serviço de API da Web.

A meta é que a lógica do domínio na camada de modelo de domínio, suas invariáveis, o modelo de dados e as regras de negócio relacionadas sejam completamente independentes das camadas de apresentação e do aplicativo. Principalmente, a camada de modelo de domínio deve não deve depender diretamente de nenhuma estrutura de infraestrutura.

### <a name="the-infrastructure-layer"></a>A camada de infraestrutura

A camada de infraestrutura é como os dados inicialmente mantidos em entidades de domínio (em memória) são mantidos em bancos de dados ou outro repositório persistente. Um exemplo é usar o código do Entity Framework Core para implementar as classes padrão do repositório que usam um DBContext para manter os dados em um banco de dados relacional.

Conforme mencionado anteriormente nos princípios de [Ignorância de Persistência](http://deviq.com/persistence-ignorance/) e [Ignorância de Infraestrutura](https://ayende.com/blog/3137/infrastructure-ignorance), a camada de infraestrutura não deve ser "contaminar" a camada de modelo de domínio. Você deve manter as classes de entidade de modelo de domínio independentes da infraestrutura que você usa para manter os dados (EF ou qualquer outra estrutura) não obtendo dependências rígidas de estruturas. Sua biblioteca de classes de camada de modelo de domínio deve ter somente o código de domínio, apenas classes de entidade [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) implementando a essência do seu software e completamente separadas de tecnologias de infraestrutura.

Assim, suas camadas ou bibliotecas e projetos de classes devem, por fim, depender da sua camada de modelo de domínio (biblioteca), não vice-versa, conforme mostra a Figura 9-7.

![](./media/image8.png)

**Figura 9-7**. Dependências entre camadas em DDD

Esse design de camada deve ser independente de cada microsserviço. Conforme observado anteriormente, você pode implementar os microsserviços mais complexos seguindo padrões DDD ao mesmo tempo em que implementa microsserviços conduzidos por dados mais simples (CRUD simples em uma única camada) de maneira mais simples.

#### <a name="additional-resources"></a>Recursos adicionais

-   **DevIQ. Princípio de Ignorância de persistência**
    [*http://deviq.com/persistence-ignorance/*](http://deviq.com/persistence-ignorance/)

-   **Oren Eini. Ignorância de infraestrutura**
    [*https://ayende.com/blog/3137/infrastructure-ignorance*](https://ayende.com/blog/3137/infrastructure-ignorance)

-   **Angel Lopez. Arquitetura em camadas no design controlado por domínio**
    [*https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/*](https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/)


>[!div class="step-by-step"]
[Anterior] (cqrs-microservice-reads.md) [Próximo] (microservice-domain-model.md)
