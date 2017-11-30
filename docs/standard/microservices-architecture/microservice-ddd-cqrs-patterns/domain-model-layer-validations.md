---
title: "Criando validações na camada de modelo de domínio"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Criando validações na camada de modelo de domínio"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f4870d0568c3539f296bcb3f577291cb0250cfca
ms.sourcegitcommit: 62d3e3e74c1b7ffa927590012c0b9f87de1b0848
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="designing-validations-in-the-domain-model-layer"></a>Criando validações na camada de modelo de domínio

No DDD, as regras de validação podem ser consideradas como invariáveis. A principal responsabilidade de uma agregação é impor invariáveis entre as alterações de estado para todas as entidades que agregam.

Entidades de domínio devem ser sempre entidades válidas. Há um determinado número de constantes para um objeto que deve ser verdadeiro. Por exemplo, um objeto de item do pedido sempre deve ter uma quantidade que deve ser um inteiro positivo, além de um nome de artigo e o preço. Portanto, a imposição de invariáveis é de responsabilidade das entidades de domínio (especialmente da agregação raiz) e um objeto de entidade não deve ser capaz de existir sem que sejam válidos. Regras invariáveis simplesmente são expressos como contratos e exceções ou notificações são geradas quando eles forem violados.

O raciocínio por trás disso é que vários bugs ocorrerem porque os objetos em um estado nunca deveria ter sido incluído. Esta é uma boa explicação de Greg Young em um [discussão on-line](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):

Vamos propor que agora temos uma SendUserCreationEmailService que leva a um perfil de usuário... como pode é racionalizar no serviço que o nome não é nulo? Podemos check-novamente? Ou mais provável... você apenas não se preocupe para verificar e "esperar o melhor" — você espera que alguém se preocupou em validá-lo antes de enviá-lo para você. É claro que, usando TDD dos testes primeiro, deve gravar é que, se enviar um cliente com um nome nulo que deve gerar um erro. Mas, quando começarmos a gravar esses tipos de testes repetidamente sabemos... "aguardar se podemos nunca nome seja nulo não temos todos esses testes"

## <a name="implementing-validations-in-the-domain-model-layer"></a>Implementando validações na camada de modelo de domínio

Validações são normalmente implementadas em construtores de entidade de domínio ou em métodos que podem atualizar a entidade. Há várias maneiras de implementar validações, como verificação de dados e aumentando exceções se a validação falhar. Também há padrões mais avançados, como usando o padrão de especificação para validações e o padrão de notificação para retornar uma coleção de erros em vez de retornar uma exceção para cada validação conforme ela ocorre.

### <a name="validating-conditions-and-throwing-exceptions"></a>Validando condições e lançando exceções

O exemplo de código a seguir mostra a abordagem mais simples de validação em uma entidade de domínio, gerando uma exceção. A tabela de referências no final desta seção, você encontrará links para implementações mais avançadas com base em padrões que discutimos anteriormente.

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

Um exemplo melhor seria demonstram a necessidade de garantir que o estado interno não foi alterado ou que todas as mutações para um método ocorreram. Por exemplo, a seguinte implementação deixará o objeto em um estado inválido:

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

Se o valor do estado é inválido, a primeira linha de endereço e cidade já tem sido alterados. Que pode tornar o endereço inválido.

Uma abordagem semelhante pode ser usada no construtor da entidade, gerando uma exceção para certificar-se de que a entidade é válido quando ele é criado.

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a>Usando atributos de validação no modelo com base em anotações de dados

Outra abordagem é usar os atributos de validação com base em anotações de dados. Atributos de validação fornecem uma maneira de configurar a validação do modelo, que é semelhante conceitualmente a validação em campos em tabelas de banco de dados. Isso inclui as restrições, como a atribuição de tipos de dados ou os campos obrigatórios. Outros tipos de validação incluem a aplicação de padrões de dados para impor regras de negócio, como um número de cartão de crédito, número de telefone ou endereço de email. Atributos de validação tornam mais fácil aplicar os requisitos.

No entanto, conforme mostrado no código a seguir, essa abordagem pode ser muito intrusiva em um modelo DDD, porque ele tem uma dependência ModelState de Microsoft.AspNetCore.Mvc.ModelState, que deve ser chamado de seus controladores MVC. Ocorre a validação do modelo antes de cada ação de controlador que está sendo invocada, e é responsabilidade do método do controlador para inspecionar o resultado da chamada ModelState e reagir de forma adequada. A decisão de usá-lo depende de como acoplado você quer que o modelo com que a infraestrutura.

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

No entanto, de um ponto de vista DDD, o modelo de domínio é melhor mantido lean com o uso de exceções em métodos de comportamento da entidade ou por implementar os padrões de notificação e especificações para impor regras de validação. Estruturas de validação como anotações de dados no ASP.NET Core ou quaisquer outras estruturas de validação como FluentValidation realizar um requisito para invocar a estrutura de aplicativo. Por exemplo, ao chamar o método ModelState nas anotações de dados, você precisa chamar controladores do ASP.NET.

Ele pode fazer sentido usar anotações de dados na camada de aplicativo em classes ViewModel (em vez de entidades de domínio) que aceita a entrada, para permitir a validação do modelo dentro da camada de interface do usuário. No entanto, isso não deve ser feito na exclusão de validação dentro do modelo de domínio.

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Validando entidades Implementando o padrão de especificação e o padrão de notificação

Por fim, uma abordagem mais elaborada para implementar a validação no modelo de domínio está implementando o padrão de especificação em conjunto com o padrão de notificação, conforme explicado em alguns dos recursos adicionais listados posteriormente.

Vale a pena mencionar que você também pode usar apenas um desses padrões — por exemplo, validação manual com instruções de controle, mas usando o padrão de notificação de pilha e retornar uma lista de erros de validação.

### <a name="using-deferred-validation-in-the-domain"></a>Usando a validação adiada no domínio

Há várias abordagens para lidar com validações adiadas no domínio. Em seu livro [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discute os na seção sobre a validação.

### <a name="two-step-validation"></a>Validação de duas etapas

Considere também a validação de duas etapas. Use a validação de nível de campo em seu comando dados transferidos DTOs (objetos) e a validação de nível de domínio dentro de suas entidades. Você pode fazer isso, retornando um objeto de resultado em vez disso, exceções para tornar mais fácil de lidar com os erros de validação.

Usando a validação de campo com anotações de dados, por exemplo, você não duplicar a definição de validação. A execução, no entanto, pode ser do lado do servidor e cliente no caso de DTOs (comandos e ViewModels, por exemplo).

## <a name="additional-resources"></a>Recursos adicionais

-   **Rachel Appel. Introdução à validação do modelo no MVC do ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)

-   **Rick Anderson. Adicionando validação**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

-   **Martin Fowler. Substituindo Lançando exceções com notificação em validações**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)

-   **Especificação e padrões de notificação**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)

-   **Lev Gorodinski. Validação no Design orientado a domínio (DDD)**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)

-   **Colin tomada. Validação de modelo de domínio**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)

-   **Jimmy Bogard. Validação em um mundo DDD**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)


>[!div class="step-by-step"]
[Anterior] (enumeração-classes-over-enum-types.md) [Avançar] (validation.md do lado do cliente)
