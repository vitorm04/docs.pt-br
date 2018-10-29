---
title: Projetando validações na camada de modelo de domínio
description: Arquitetura de microsserviços .NET para aplicativos .NET em contêineres | Criando validações na camada de modelo de domínio
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 6ff325bb062da2ebff815fc847d2247707a0bf7f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188047"
---
# <a name="designing-validations-in-the-domain-model-layer"></a>Projetando validações na camada de modelo de domínio

Em DDD, as regras de validação podem ser consideradas invariáveis. A principal responsabilidade de uma agregação é impor invariáveis entre as alterações de estado para todas as entidades dentro daquela agregação.

Entidades de domínio devem ser sempre entidades válidas. Existe um determinado número de invariáveis para um objeto que devem ser sempre verdadeiras. Por exemplo, um objeto de item do pedido sempre deve ter uma quantidade que deve ser um inteiro positivo, além de um nome de artigo e preço. Portanto, a imposição de invariáveis é de responsabilidade das entidades de domínio (especialmente da raiz de agregação) e um objeto de entidade não deve ser capaz de existir sem ser válido. Regras invariáveis simplesmente são expressas como contratos e exceções ou notificações são geradas quando elas são violadas.

O raciocínio por trás disso é que vários bugs ocorrerem porque os objetos estão em um estado em que nunca deveriam ter ficado. A seguir está uma boa explicação de Greg Young em uma [discussão online](https://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):

Vamos propor que agora temos um SendUserCreationEmailService que usa um UserProfile..., como podemos racionalizar nesse serviço que o Nome não é nulo? Podemos verificar novamente? Ou, mais provável… você apenas não se preocupa em verificar e "espera pelo melhor": você espera que alguém tenha se preocupado em validá-lo antes de enviá-lo a você. É claro que, usando TDD, um dos primeiros testes que devemos escrever é que, se eu enviar um cliente com um nome nulo, isso deverá gerar um erro. Porém, quando começarmos a escrever esses tipos de testes repetidamente, percebemos… "espere, se nunca tivéssemos permitido que o nome se tornasse nulo, não teríamos todos esses testes"

## <a name="implementing-validations-in-the-domain-model-layer"></a>Implementando validações na camada de modelo de domínio

As validações normalmente são implementadas em construtores de entidade de domínio ou em métodos que podem atualizar a entidade. Existem várias maneiras de implementar validações, como verificar dados e aumentar exceções se a validação falhar. Também há padrões mais avançados, como usar o padrão de Especificação para validações e o padrão de Notificação para retornar uma coleção de erros, em vez de retornar uma exceção para cada validação conforme ela ocorre.

### <a name="validating-conditions-and-throwing-exceptions"></a>Validando condições e gerando exceções

O exemplo de código a seguir mostra a abordagem mais simples de validação em uma entidade de domínio gerando uma exceção. Na tabela de referências no final desta seção, você encontrará links para implementações mais avançadas com base nos padrões que discutimos anteriormente.

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

Um exemplo melhor seria demonstrar a necessidade de garantir que o estado interno não tenha mudado ou que todas as mutações para um método ocorreram. Por exemplo, a implementação a seguir deixará o objeto em um estado inválido:

```csharp
public void SetAddress(string line1, string line2,
    string city, string state, int zip)
{
    _shipingAddress.line1 = line1 ?? throw new ...
    _shippingAddress.line2 = line2;
    _shippingAddress.city = city ?? throw new ...
    _shippingAddress.state = (IsValid(state) ? state : throw new …);
}
```

Se o valor do estado for inválido, a primeira linha de endereço e a cidade já terão sido alteradas. Isso pode tornar o endereço inválido.

Uma abordagem semelhante pode ser usada no construtor da entidade, gerando uma exceção para garantir que a entidade seja válida quando for criada.

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a>Usando atributos de validação no modelo com base em anotações de dados

Outra abordagem é usar os atributos de validação com base em anotações de dados. Os atributos de validação oferecem uma maneira de configurar a validação do modelo; isso é conceitualmente semelhante à validação em campos de tabelas de banco de dados. Isso inclui restrições, como atribuição de tipos de dados ou campos obrigatórios. Outros tipos de validação incluem a aplicação de padrões a dados para impor regras de negócio, como um número de cartão de crédito, número de telefone ou endereço de email. Atributos de validação tornam fácil impor os requisitos.

No entanto, conforme mostra o código a seguir, essa abordagem pode ser muito invasiva em um modelo DDD, porque tem uma dependência ModelState.IsValid de Microsoft.AspNetCore.Mvc.ModelState, que você deve chamar de seus controladores MVC. A validação do modelo ocorre antes de cada ação de controlador ser invocada, e é responsabilidade do método do controlador inspecionar o resultado da chamada ModelState.IsValid e reagir de maneira adequada. A decisão de usá-lo depende de quão firmemente acoplado você deseja que o modelo esteja àquela infraestrutura.

```csharp
using System.ComponentModel.DataAnnotations;
// Other using statements ...
// Entity is a custom base class which has the ID
public class Product : Entity
{
    [Required]
    [StringLength(100)]
    public string Title { get; private set; }

    [Required]
    [Range(0, 999.99)]
    public decimal Price { get; private set; }

    [Required]
    [VintageProduct(1970)]
    [DataType(DataType.Date)]
    public DateTime ReleaseDate { get; private set; }

    [Required]
    [StringLength(1000)]
    public string Description { get; private set; }

    // Constructor...
    // Additional methods for entity logic and constructor...
}
```

No entanto, de um ponto de vista de DDD, o modelo de domínio é mantido mais enxuto com o uso de exceções em seus métodos de comportamento da entidade ou implementando os padrões de Especificação e Notificação para impor regras de validação. Estruturas de validação como anotações de dados no ASP.NET Core ou quaisquer outras estruturas de validação, como FluentValidation, têm um requisito de invocar a estrutura do aplicativo. Por exemplo, ao chamar o método ModelState.IsValid nas anotações de dados, você precisa invocar controladores do ASP.NET.

Pode fazer sentido usar anotações de dados na camada de aplicativo em classes ViewModel (em vez de entidades de domínio) que aceitem a entrada para permitir a validação do modelo na camada da interface do usuário. No entanto, isso não deve ser feito na exclusão de validação dentro do modelo de domínio.

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Validando entidades implementando o padrão de Especificação e o padrão de Notificação

Por fim, uma abordagem mais elaborada para implementar a validação no modelo de domínio é implementando o padrão de Especificação em conjunto com o padrão de Notificação, conforme explicado em alguns dos recursos adicionais listados posteriormente.

Vale a pena mencionar que você também pode usar apenas um desses padrões — por exemplo, validação manual com instruções de controle, mas usando o padrão de Notificação para empilhar e retornar uma lista de erros de validação.

### <a name="using-deferred-validation-in-the-domain"></a>Usando a validação adiada no domínio

Existem várias abordagens para lidar com validações adiadas no domínio. Em seu livro [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577) (Implementando design controlado por domínio), Vaughn Vernon discute isso na seção sobre a validação.

### <a name="two-step-validation"></a>Validação de duas etapas

Considere também a validação de duas etapas. Use a validação em nível de campo em seu comando de DTOs (Objetos de Transferência de Dados) e a validação em nível de domínio dentro de suas entidades. Você pode fazer isso retornando um objeto de resultado em vez de exceções para tornar mais fácil lidar com os erros de validação.

Usando a validação de campo com anotações de dados, por exemplo, você não duplica a definição de validação. A execução, no entanto, pode estar do lado do servidor e do lado do cliente no caso de DTOs (comandos e ViewModels, por exemplo).

## <a name="additional-resources"></a>Recursos adicionais

-   **Rachel Appel. Introdução à validação do modelo no ASP.NET Core MVC**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)

-   **Rick Anderson. Adicionando validação**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

-   **Martin Fowler. Substituindo a geração de exceções pela notificação em validações**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)

-   **Especificação e padrões de notificação**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)

-   **Lev Gorodinski. Validação no DDD (Design Controlado por Domínio)**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)

-   **Colin Jack. Validação do modelo de domínio**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)

-   **Jimmy Bogard. Validação em um mundo em DDD**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)


>[!div class="step-by-step"]
[Anterior](enumeration-classes-over-enum-types.md)
[Próximo](client-side-validation.md)
