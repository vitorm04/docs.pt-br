---
title: "Criar um modelo de domínio de microsserviço"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Criar um modelo de domínio de microsserviço"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 455a2c5a39fb9b765b557610ab108f8c75882dbd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="designing-a-microservice-domain-model"></a>Criar um modelo de domínio de microsserviço

*Definir um modelo de domínio avançado para cada microsserviço de negócios ou contexto limitado*

Seu objetivo é criar um modelo de domínio coesa único para cada microsserviço de negócios ou contexto limitado (BC). Tenha em mente, no entanto, que uma continuidade de negócios ou microsserviço de negócios, às vezes, pode ser composto de vários serviços físicos que compartilham um modelo de domínio único. O modelo de domínio deve capturar a regras, o comportamento, idioma de negócios e restrições do contexto associado único ou microsserviço de negócios que ele representa.

## <a name="the-domain-entity-pattern"></a>O padrão de entidade de domínio

Entidades representam objetos de domínio e principalmente são definidas por sua identidade, continuidade e persistência ao longo do tempo e não apenas pelos atributos que compõem a eles. Como Eric Evans afirma, "um objeto definido, basicamente, por sua identidade é denominado entidade." Entidades são muito importantes no modelo de domínio, pois eles são a base para um modelo. Portanto, você deve identificar e criá-las com cuidado.

*Identidade de uma entidade pode cruzar vários microservices ou contextos limitada.*

A mesma identidade (embora não é a mesma entidade) podem ser modelados em vários contextos limitada ou microservices. No entanto, que não significa que a mesma entidade, com os mesmos atributos e lógica poderia ser implementada em vários contextos limitada. Em vez disso, as entidades em cada contexto limitado limitam seus atributos e os comportamentos para aqueles necessários no domínio do contexto associado.

Por exemplo, a entidade de comprador talvez tenha a maioria dos atributos de uma pessoa que estão definidos na entidade no microsserviço perfil ou a identidade, incluindo a identidade do usuário. Mas a entidade de comprador no microsserviço a ordenação pode ter menos de atributos, porque somente determinados dados comprador estão relacionados ao processo de ordem. O contexto de cada microsserviço ou contexto limitado afeta o seu modelo de domínio.

*Entidades de domínio devem implementar o comportamento, além de implementar os atributos de dados*

Uma entidade de domínio no DDD deve implementar a lógica do domínio ou o comportamento relacionado aos dados de entidade (o objeto acessado na memória). Por exemplo, como parte de uma classe de entidade de ordem, você deve ter lógica de negócios e implementadas como métodos para tarefas como adicionar um item do pedido, a validação de dados e o cálculo do total de operações. Métodos da entidade se encarregar as regras da entidade em vez de ter essas regras disseminadas por camada de aplicativo e invariáveis.

Figura 9-8 mostra uma entidade de domínio que implementa não apenas atributos de dados, mas as operações ou métodos com a lógica do domínio relacionadas.

![](./media/image9.png)

**Figura 9-8**. Exemplo de um projeto de entidade de domínio implementando dados mais comportamento

É claro que, às vezes, você pode ter entidades que não implementam qualquer lógica como parte da classe da entidade. Isso pode ocorrer em entidades filhas dentro de uma agregação se a entidade filho não tiver nenhuma lógica especial porque a maioria da lógica está definida na raiz da agregação. Se você tiver um microsserviço complexas com muita lógica implementada em classes de serviço em vez de às entidades de domínio, você poderia falha no modelo de domínio anêmica, como explicado na seção a seguir.

### <a name="rich-domain-model-versus-anemic-domain-model"></a>Modelo de domínio avançado em comparação com o modelo de domínio anêmica

Em sua postagem [AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html), Martin Fowler descreve um modelo de domínio anêmica desta forma:

O sintoma básico de um modelo de domínio anêmica é que no primeiro um pouco parece que a situação real. Existem objetos, muitos nomeado de acordo com os nomes no espaço de domínio e esses objetos estão conectados com o relações avançadas e a estrutura que têm modelos de domínio true. Catch é fornecida quando você observar o comportamento e perceber que há praticamente qualquer comportamento nesses objetos, tornando-os pouco mais pacotes de getters e setters.

É claro que, quando você usa um modelo de domínio anêmica, esses modelos de dados serão usados de um conjunto de objetos de serviço (tradicionalmente nomeada a *camada comercial*) que capture toda a lógica de negócios ou de domínio. A camada de negócios fica na parte superior do modelo de dados e usa o modelo de dados, assim como os dados.

O modelo de domínio anêmica é um design de estilo de procedimento. Objetos de entidade anêmica não são objetos reais, porque eles não têm comportamento (métodos). Mantenham somente propriedades de dados e, portanto, não é orientada a objeto de design. Colocando todo o comportamento de expansão em objetos de serviço (a camada de negócios) essencialmente acabar com [código espaguete](https://en.wikipedia.org/wiki/Spaghetti_code) ou [scripts de transação](https://martinfowler.com/eaaCatalog/transactionScript.html), e, portanto, você perde as vantagens que um modelo de domínio fornece.

Independentemente se o microsserviço ou contexto associado é muito simple (um serviço CRUD), o modelo de domínio anêmica na forma de objetos de entidade com apenas as propriedades de dados pode ser suficiente, e talvez não seja válido implementar os padrões mais complexos de DDD. Nesse caso, ele poderá ser simplesmente um modelo de persistência, porque você intencionalmente criou uma entidade com apenas os dados para fins CRUD.

É por isso que microservices arquiteturas são perfeitas para uma abordagem de arquitetura várias dependendo de cada contexto associado. Por exemplo, eShopOnContainers, o ordenação microsserviço implementa os padrões de DDD, mas o catálogo microsserviço, que é um serviço CRUD simples, não.

Algumas pessoas dizem que o modelo de domínio anêmica é um padrão de um. Isso realmente depende se você estiver implementando. Se o microsserviço que você está criando é simples suficiente (por exemplo, um serviço CRUD), o modelo de domínio anêmica não é um antia padrão de seguir. No entanto, se você precisa lidar com a complexidade do domínio do microsserviço que tem várias constantes de regras de negócio, o modelo de domínio anêmica pode ser um antipadrão do contexto associado ou microsserviço. Nesse caso, criando-o como um conjunto avançado modelo com entidades que contém dados mais comportamento, bem como implementar os padrões DDD adicionais (agregações, objetos de valor, etc.) pode ter enormes benefícios para o sucesso a longo prazo de tal um microsserviço.

#### <a name="additional-resources"></a>Recursos adicionais

-   **DevIQ. Entidade de domínio**
    [*http://deviq.com/entity/*](http://deviq.com/entity/)

-   **Martin Fowler. O modelo de domínio**
    [*https://martinfowler.com/eaaCatalog/domainModel.html*](https://martinfowler.com/eaaCatalog/domainModel.html)

-   **Martin Fowler. O modelo de domínio anêmica**

    <https://martinfowler.com/bliki/AnemicDomainModel.HTML>

### <a name="the-value-object-pattern"></a>O padrão de objeto de valor

Conforme observado a Eric Evans, "muitos objetos não possuem identidade conceitual. Esses objetos descrevem a certas características de um ponto."

Uma entidade requer uma identidade, mas há muitos objetos em um sistema que não, como o padrão do objeto de valor. Um objeto de valor é um objeto com nenhuma identidade conceitual que descreve um aspecto de domínio. Esses são objetos que você cria uma instância para representar os elementos de design que apenas temporariamente lhe interessam. Você gosta *que* , não são *que* estiverem. Exemplos incluem números e cadeias de caracteres, mas também podem ser conceitos de nível superior como grupos de atributos.

Algo que é uma entidade em um microsserviço não pode ser uma entidade em outro microsserviço, como no segundo caso, o contexto associado pode ter um significado diferente. Por exemplo, um endereço em um aplicativo de comércio eletrônico pode não ter uma identidade, desde que ele pode representar apenas um grupo de atributos de perfil do cliente para uma pessoa ou empresa. Nesse caso, o endereço deve ser classificado como um objeto de valor. No entanto, em um aplicativo para uma empresa de utilitário de energia elétrica, o endereço do cliente pode ser importante para o domínio da empresa. Portanto, o endereço deve ter uma identidade para que o sistema de cobrança pode ser vinculado diretamente para o endereço. Nesse caso, um endereço deve ser classificado como uma entidade de domínio.

Uma pessoa com um nome e sobrenome geralmente é uma entidade como uma pessoa tem identidade, mesmo se o nome e sobrenome coincidirem com outro conjunto de valores, como se esses nomes também se refere a uma pessoa diferente.

Objetos de valor são difíceis de gerenciar em bancos de dados relacionais e ORMs como EF, enquanto o documento orientado a bancos de dados são mais fáceis de implementar e usar.

#### <a name="additional-resources"></a>Recursos adicionais

-   **Martin Fowler. Padrão de objeto de valor**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **Valor de objeto**
    [*http://deviq.com/value-object/*](http://deviq.com/value-object/)

-   **Valor de objetos no Driven Development**
    [*https://leanpub.com/tdd-ebook/read\#leanpub-auto-objetos de valor*](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)

-   **Eric Evans. Design controlado por domínio: Lidar com a complexidade do Centro de Software.** (Livro; inclui uma discussão sobre objetos de valor) [ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

### <a name="the-aggregate-pattern"></a>O padrão de agregação

Um modelo de domínio contém clusters de entidades de dados diferentes e os processos que podem controlar uma área significativa de funcionalidades, como inventário ou a realização de ordem. Uma unidade DDD mais refinada é a agregação, que descreve um cluster ou o grupo de entidades e os comportamentos que podem ser tratados como uma unidade coesa.

Normalmente, você define uma agregação com base em transações que você precisa. Um exemplo clássico é um pedido que também contém uma lista de itens do pedido. Geralmente, um item do pedido será uma entidade. Mas é uma entidade filho dentro a agregação de ordem, que também conterá a entidade pedido como sua entidade raiz, geralmente chamada de uma raiz de agregação.

Pode ser difícil identificar agregações. Uma agregação é um grupo de objetos que devem ser consistentes em conjunto, mas apenas não é possível selecionar um grupo de objetos e rotular uma agregação. Você deve iniciar com um conceito de domínio e pensar sobre as entidades que são usadas nas transações mais comuns relacionadas a esse conceito. As entidades que precisam ser transacionalmente consistente são o que forma uma agregação. Pensar sobre as operações de transação provavelmente é a melhor maneira de identificar as agregações.

### <a name="the-aggregate-root-or-root-entity-pattern"></a>O padrão de raiz de agregação ou entidade raiz

Uma agregação é composta pelo menos uma entidade: a raiz de agregação, também chamada entidade raiz ou ientity primário. Além disso, ele pode ter várias entidades filhas e objetos de valor, com todas as entidades e objetos trabalham juntas para implementar transações e comportamento necessário.

A finalidade de uma raiz agregada é garantir a consistência da agregação; ele deve ser o único ponto de entrada para atualizações para a agregação através dos métodos ou operações de classe raiz em conjunto. Você deve fazer alterações às entidades a agregação apenas por meio da raiz de agregação. É guardião de consistência da agregação, levando em conta todas as regras de consistência que talvez você precise estar de acordo com seu juntos e invariáveis. Se você alterar um objeto de entidade ou um valor do filho independentemente, a raiz de agregação não pode garantir que a agregação está em um estado válido. Seria parecida com uma tabela com um segmento flexível. Mantendo a consistência é o principal objetivo da raiz da agregação.

Na Figura 9-9, você pode ver as agregações de exemplo como o comprador de agregação, que contém uma única entidade (a raiz de agregação comprador). A agregação de ordem contém várias entidades e um objeto de valor.

![](./media/image10.png)

**Figura 9-9**. Exemplo de agregações com várias ou únicas entidades

Observe que a agregação de comprador pode ter entidades filho adicionais, dependendo de seu domínio, como ocorre o ordenação microsserviço no aplicativo eShopOnContainers referência. Figura 9-9 apenas ilustra um caso em que o comprador tem uma única entidade, como um exemplo de uma agregação que contém somente uma raiz de agregação.

Para manter a separação de agregações e manter limites claros entre eles, é uma prática recomendada em um modelo de domínio DDD para impedir a navegação direta entre agregações e tendo apenas o campo de chave estrangeira (FK), conforme implementado o [ Ordenação de modelo de domínio de microsserviço](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs) em eShopOnContainers. A entidade de ordem tem apenas um campo FK para o comprador, mas não uma propriedade de navegação principal EF, conforme mostrado no código a seguir:

```csharp
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId; //FK pointing to a different aggregate root
    public OrderStatus OrderStatus { get; private set; }
}
```

Identificando e trabalhar com agregações requer pesquisa e experiência. Para obter mais informações, consulte a lista de recursos adicionais a seguir.

#### <a name="additional-resources"></a>Recursos adicionais

-   **Vaughn Vernon. Design de agregação eficaz - parte i: uma única agregação de modelagem**
    [*https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD\_COMMUNITY\_ensaio\_ AGREGAÇÕES\_parte\_pdf 1.*](https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_1.pdf)

-   **Vaughn Vernon. Design de agregação eficaz - parte II: Fazendo agregações funcionam em conjunto**
    *<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_2.pdf>*

-   **Vaughn Vernon. Design de agregação eficaz - parte III: Obtenção de informações por meio da descoberta**
    *<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_3.pdf>*

-   **Sergey Grybniak. Padrões de Design táticas DDD**
    [*https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part*](https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part)

-   **Carlos Richardson. Desenvolvendo Microservices transacional usando agregações**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson)

-   **DevIQ. O padrão de agregação**
    [*http://deviq.com/aggregate-pattern/*](http://deviq.com/aggregate-pattern/)


>[!div class="step-by-step"]
[Anterior] (ddd-orientado-microservice.md) [Avançar] (net-core-microsserviço-domínio-model.md)
