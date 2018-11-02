---
title: Criando um modelo de domínio de microsserviço
description: Arquitetura de microsserviços .NET para aplicativos .NET em contêineres | Criando um modelo de domínio de microsserviço
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/09/2017
ms.openlocfilehash: 9a54679fc28bb2adf803a38fe5e43f67048a4cfd
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50048470"
---
# <a name="designing-a-microservice-domain-model"></a>Criando um modelo de domínio de microsserviço

*Definir um modelo de domínio avançado para cada microsserviço de negócios ou Contexto Limitado*

Sua meta é criar um único modelo de domínio coeso para cada microsserviço de negócios ou BC (Contexto Limitado). No entanto, tenha em mente que um microsserviço de BC ou de continuidade de negócios, às vezes, pode ser composto por vários serviços físicos que compartilham um único modelo de domínio. O modelo de domínio precisa capturar as regras, o comportamento, a linguagem de negócios e as restrições do único Contexto Limitado ou microsserviço de negócios que ele representa.

## <a name="the-domain-entity-pattern"></a>O padrão de entidade de domínio

As entidades representam objetos de domínio e são definidas principalmente pela identidade, a continuidade e a persistência ao longo do tempo e não apenas pelos atributos que as compõem. Como Eric Evans afirma, "um objeto definido principalmente pela sua identidade é chamado de entidade”. As entidades são muito importantes no modelo de domínio, pois elas são a base para um modelo. Portanto, você deve identificá-las e criá-las com cuidado.

*A identidade de uma entidade pode cruzar vários microsserviços ou contextos limitados.*

A mesma identidade (mas não a mesma entidade) pode ser modelada em vários Contextos Limitados ou microsserviços. No entanto, isso não significa que a mesma entidade, com os mesmos atributos e a mesma lógica, possa ser implementada em vários Contextos Limitados. Nesse caso, as entidades em cada Contexto Limitado limitam seus atributos e comportamentos aos que são necessários no domínio do Contexto Limitado.

Por exemplo, a entidade de comprador talvez tenha a maioria dos atributos de uma pessoa que estão definidos na entidade de usuário no microsserviço de perfil ou de identidade, incluindo a identidade. Mas a entidade de comprador no microsserviço de pedidos pode ter menos atributos, porque somente determinados dados do comprador estão relacionados ao processo de pedido. O contexto de cada microsserviço ou o Contexto Limitado afeta o modelo de domínio.

*As entidades de domínio precisam implementar o comportamento, além de implementar os atributos de dados*

Uma entidade de domínio no DDD precisa implementar a lógica do domínio ou o comportamento relacionado aos dados da entidade (o objeto acessado na memória). Por exemplo, como parte de uma classe de entidade de pedido, você precisa ter a lógica de negócios e as operações implementadas como métodos para tarefas como adicionar um item de pedido, validação de dados e cálculo de total. Os métodos da entidade encarregam-se das invariáveis e das regras da entidade em vez de disseminar essas regras na camada de aplicativo.

A Figura 9-8 mostra uma entidade de domínio que, além de implementar os atributos de dados, também implementa as operações ou os métodos com a lógica de domínio relacionada.

![](./media/image9.png)

**Figura 9-8**. Exemplo de um projeto de entidade de domínio implementando dados e também comportamento

Obviamente, também é possível haver entidades que não implementam nenhuma lógica como parte da classe da entidade. Isso poderá ocorrer em entidades filhas dentro de uma agregação se a entidade filha não tiver nenhuma lógica especial porque a maioria da lógica está definida na raiz da agregação. Se houver um microsserviço complexo com muita lógica implementada em classes de serviço e não nas entidades de domínio, você poderá cair no modelo de domínio anêmico, que será explicado na próxima seção.

### <a name="rich-domain-model-versus-anemic-domain-model"></a>Modelo de domínio avançado em comparação com o modelo de domínio anêmico

Em sua postagem [AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html), Martin Fowler descreve um modelo de domínio fraco desta forma:

O sintoma básico de um modelo de domínio anêmico é que, à primeira vista, ele parece real. Existem objetos, muitos nomeados de acordo com os nomes no espaço de domínio, conectados com as relações avançadas e a estrutura que os modelos de domínio verdadeiros têm. A verdade aparece quando você observa o comportamento e percebe que não há praticamente nenhum comportamento nesses objetos, ou seja, eles não passam de pacotes de getters e setters.

É claro que, quando você usar um modelo de domínio anêmico, serão usados os modelos de dados de um conjunto de objetos de serviço (tradicionalmente chamado de *camada comercial*) que captura toda a lógica de negócios ou do domínio. A camada de negócios fica acima do modelo de dados e usa o modelo de dados apenas como dados.

O modelo de domínio anêmico é apenas um design de estilo de procedimento. Os objetos da entidade anêmica não são objetos reais, porque eles não têm comportamento (métodos). Eles apenas mantêm as propriedades dos dados e, portanto, não são de design orientado a objeto. Ao colocar todo o comportamento nos objetos de serviço (na camada de negócios), basicamente, o resultado será um [código espaguete](https://en.wikipedia.org/wiki/Spaghetti_code) ou [scripts de transação](https://martinfowler.com/eaaCatalog/transactionScript.html) e, portanto, você perderá as vantagens que um modelo de domínio oferece.

De qualquer maneira, se o microsserviço ou o Contexto Limitado for muito simples (um serviço de CRUD), o modelo de domínio anêmico na forma de objetos de entidade apenas com as propriedades dos dados já poderá ser suficiente e talvez não compense implementar os padrões mais complexos de DDD. Nesse caso, ele será simplesmente um modelo de persistência, porque você criou uma entidade intencionalmente apenas com os dados para fins de CRUD.

É por isso que as arquiteturas de microsserviços são perfeitas para uma abordagem de várias arquiteturas, dependendo de cada Contexto Limitado. Por exemplo, no eShopOnContainers, o microsserviço de pedidos implementa os padrões de DDD, mas o microsserviço de catálogo, que é um serviço de CRUD simples, não implementa.

Algumas pessoas dizem que o modelo de domínio anêmico é um antipadrão. Isso realmente depende do que está sendo implementando. Se o microsserviço que você estiver criando for simples o suficiente (por exemplo, um serviço de CRUD), seguir o modelo de domínio anêmico não será um antipadrão. No entanto, se você precisar lidar com a complexidade de um domínio de microsserviço que tenha várias regras de negócios em constante mudança, o modelo de domínio anêmico poderá ser um antipadrão para esse microsserviço ou Contexto Limitado. Nesse caso, criá-lo como um modelo avançado com entidades contendo dados e comportamentos, bem como implementar os padrões de DDD adicionais (agregações, objetos de valor, etc.) pode trazer enormes benefícios para o sucesso a longo prazo desse microsserviço.

#### <a name="additional-resources"></a>Recursos adicionais

-   **DevIQ. Entidade de domínio**
    [*https://deviq.com/entity/*](https://deviq.com/entity/)

-   **Martin Fowler. O modelo de domínio**
    [*https://martinfowler.com/eaaCatalog/domainModel.html*](https://martinfowler.com/eaaCatalog/domainModel.html)

-   **Martin Fowler. The Anemic Domain Model** (O modelo de domínio anêmico)

    <https://martinfowler.com/bliki/AnemicDomainModel.html>

### <a name="the-value-object-pattern"></a>O padrão de objeto de valor

Conforme observado por Eric Evans, "Muitos objetos não têm uma identidade conceitual. Esses objetos descrevem certas características de algo.”

Uma entidade requer uma identidade, mas há muitos objetos em um sistema que não requerem, como o padrão de objeto de valor. Um objeto de valor é um objeto sem nenhuma identidade conceitual que descreve um aspecto de domínio. Esses são objetos dos quais uma instância é criada para representar os elementos de design que interessam apenas temporariamente. Importa *o que* eles são e não *quem* são. Exemplos incluem números e cadeias de caracteres, mas também podem ser conceitos de nível superior como grupos de atributos.

Algo que é uma entidade em um microsserviço pode não ser uma entidade em outro microsserviço, porque no segundo caso, o Contexto Limitado pode ter um significado diferente. Por exemplo, um endereço em um aplicativo de comércio eletrônico pode não ter uma identidade, pois talvez ele apenas represente um grupo de atributos do perfil do cliente de uma pessoa ou empresa. Nesse caso, o endereço deve ser classificado como um objeto de valor. No entanto, em um aplicativo de uma empresa utilitária de energia elétrica, o endereço do cliente pode ser importante para o domínio de negócios. Portanto, o endereço precisa ter uma identidade para que o sistema de cobrança possa ser vinculado diretamente ao endereço. Nesse caso, o endereço deve ser classificado como uma entidade de domínio.

Uma pessoa com um nome e um sobrenome geralmente é uma entidade, porque a pessoa tem uma identidade, mesmo se o nome e o sobrenome coincidirem com outro conjunto de valores, por exemplo, se esses nomes também se referirem a uma outra pessoa.

Os objetos de valor são difíceis de gerenciar em bancos de dados relacionais e em ORMs, como o EF, mas em bancos de dados orientados a documentos eles são mais fáceis de implementar e usar.

#### <a name="additional-resources"></a>Recursos adicionais

-   **Martin Fowler. Padrão de objeto de valor**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **Objeto de valor**
    [*https://deviq.com/value-object/*](https://deviq.com/value-object/)

-   **Objetos de valor no Desenvolvimento Orientado por Testes**
    [*https://leanpub.com/tdd-ebook/read\#leanpub-auto-value-objects*](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)

-   **Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software (Design orientado por domínio: lidando com a complexidade no núcleo do software).** (Livro; inclui uma discussão sobre objetos de valor) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

### <a name="the-aggregate-pattern"></a>O padrão de agregação

Um modelo de domínio contém diferentes clusters de entidades de dados e processos que podem controlar uma área significativa de funcionalidades, como inventário ou execução de pedidos. Uma unidade de DDD mais refinada é a agregação, que descreve um cluster ou o grupo de entidades e os comportamentos que podem ser tratados como uma unidade coesa.

Normalmente, a agregação é definida com base nas transações que são necessárias. Um exemplo clássico é um pedido que também contém uma lista de itens do pedido. Geralmente, um item do pedido será uma entidade. Mas ela será uma entidade filha dentro da agregação de pedido, que também conterá a entidade de pedido como entidade raiz, geralmente chamada de raiz de agregação.

Pode ser difícil identificar agregações. Uma agregação é um grupo de objetos que precisam ser consistentes em conjunto, mas não basta apenas selecionar um grupo de objetos e rotulá-lo como uma agregação. Você precisa começar com um conceito de domínio e pensar sobre as entidades que são usadas nas transações mais comuns relacionadas a esse conceito. As entidades que precisam ser consistentes entre as transações são as que formam uma agregação. Pensar sobre as operações de transação provavelmente é a melhor maneira de identificar as agregações.

### <a name="the-aggregate-root-or-root-entity-pattern"></a>O padrão de raiz de agregação ou de entidade raiz

Uma agregação é composta por pelo menos uma entidade: a raiz de agregação, também chamada de entidade raiz ou entidade principal. Além disso, ela pode ter várias entidades filhas e objetos de valor, com todas as entidades e os objetos trabalhando juntos para implementar as transações e os comportamentos necessários.

A finalidade de uma raiz de agregação é garantir a consistência da agregação. Ela deve ser o único ponto de entrada para as atualizações da agregação por meio de métodos ou operações na classe raiz de agregação. Você deve fazer alterações nas entidades na agregação apenas por meio da raiz de agregação. Ela é a proteção da consistência da agregação, levando em conta todas as invariáveis e as regras de consistência que devem ser obedecidas na agregação. Se você alterar uma entidade filha ou um objeto de valor de forma independente, a raiz de agregação não poderá garantir que a agregação esteja em um estado válido. Isso seria semelhante a uma tabela com um segmento flexível. Manter a consistência é o principal objetivo da raiz de agregação.

Na Figura 9-9, veja as agregações de exemplo, como a agregação de comprador, que contém uma única entidade (a raiz de agregação de comprador). A agregação de pedido contém várias entidades e um objeto de valor.

![](./media/image10.png)

**Figura 9-9**. Exemplo de agregações com uma única entidade ou com várias entidades

Observe que a agregação de comprador poderá ter entidades filhas adicionais, dependendo do domínio, como ocorre no microsserviço de pedidos no aplicativo eShopOnContainers de referência. A Figura 9-9 apenas ilustra um caso em que o comprador tem uma única entidade, como exemplo de uma agregação que contém somente uma raiz de agregação.

Para manter a separação de agregações e manter limites claros entre elas, uma prática recomendada em um modelo de domínio de DDD é não permitir a navegação direta entre as agregações e ter apenas o campo de FK (chave estrangeira), como foi implementado no [Modelo de domínio do microsserviço de pedidos](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs) no eShopOnContainers. A entidade de pedido tem apenas um campo FK para o comprador, mas não uma propriedade de navegação do EF Core, conforme é mostrado no código a seguir:

```csharp
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId; //FK pointing to a different aggregate root
    public OrderStatus OrderStatus { get; private set; }
    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;
    // ... Additional code
}
```

Para identificar e trabalhar com agregações é necessário fazer pesquisas e ter experiência. Para obter mais informações, consulte a lista de Recursos adicionais a seguir.

#### <a name="additional-resources"></a>Recursos adicionais

-   **Vaughn Vernon. Design de agregação eficaz – parte I: modelando uma única agregação**
    [*https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD\_COMMUNITY\_ESSAY\_AGGREGATES\_PART\_1.pdf*](https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_1.pdf)

-   **Vaughn Vernon. Design de agregação eficaz – parte II: fazendo com que agregações trabalhem em conjunto**
    [*https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_2.pdf*](https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_2.pdf)

-   **Vaughn Vernon. Design de agregação eficaz – parte III: obtendo insights por meio da descoberta**
    [*https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_3.pdf*](https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_3.pdf)

-   **Sergey Grybniak. Padrões de design tático em DDD**
    [*https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part*](https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part)

-   **Chris Richardson. Desenvolvendo microsserviços transacionais usando agregações**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson)

-   **DevIQ. O padrão de agregação**
    [*https://deviq.com/aggregate-pattern/*](https://deviq.com/aggregate-pattern/)

>[!div class="step-by-step"]
[Anterior](ddd-oriented-microservice.md)
[Próximo](net-core-microservice-domain-model.md)
