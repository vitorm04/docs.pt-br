---
title: "Projetando validações na camada de modelo de domínio"
description: "Arquitetura de microsserviços .NET para aplicativos .NET em contêineres | Criando validações na camada de modelo de domínio"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e7a111ce20039f8c87d3c3d63efdeaf38a4e1e96
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="designing-validations-in-the-domain-model-layer"></a><span data-ttu-id="09326-104">Projetando validações na camada de modelo de domínio</span><span class="sxs-lookup"><span data-stu-id="09326-104">Designing validations in the domain model layer</span></span>

<span data-ttu-id="09326-105">Em DDD, as regras de validação podem ser consideradas invariáveis.</span><span class="sxs-lookup"><span data-stu-id="09326-105">In DDD, validation rules can be thought as invariants.</span></span> <span data-ttu-id="09326-106">A principal responsabilidade de uma agregação é impor invariáveis entre as alterações de estado para todas as entidades dentro daquela agregação.</span><span class="sxs-lookup"><span data-stu-id="09326-106">The main responsibility of an aggregate is to enforce invariants across state changes for all the entities within that aggregate.</span></span>

<span data-ttu-id="09326-107">Entidades de domínio devem ser sempre entidades válidas.</span><span class="sxs-lookup"><span data-stu-id="09326-107">Domain entities should always be valid entities.</span></span> <span data-ttu-id="09326-108">Existe um determinado número de invariáveis para um objeto que devem ser sempre verdadeiras.</span><span class="sxs-lookup"><span data-stu-id="09326-108">There are a certain number of invariants for an object that should always be true.</span></span> <span data-ttu-id="09326-109">Por exemplo, um objeto de item do pedido sempre deve ter uma quantidade que deve ser um inteiro positivo, além de um nome de artigo e preço.</span><span class="sxs-lookup"><span data-stu-id="09326-109">For example, an order item object always has to have a quantity that must be a positive integer, plus an article name and price.</span></span> <span data-ttu-id="09326-110">Portanto, a imposição de invariáveis é de responsabilidade das entidades de domínio (especialmente da raiz de agregação) e um objeto de entidade não deve ser capaz de existir sem ser válido.</span><span class="sxs-lookup"><span data-stu-id="09326-110">Therefore, invariants enforcement is the responsibility of the domain entities (especially of the aggregate root) and an entity object should not be able to exist without being valid.</span></span> <span data-ttu-id="09326-111">Regras invariáveis simplesmente são expressas como contratos e exceções ou notificações são geradas quando elas são violadas.</span><span class="sxs-lookup"><span data-stu-id="09326-111">Invariant rules are simply expressed as contracts, and exceptions or notifications are raised when they are violated.</span></span>

<span data-ttu-id="09326-112">O raciocínio por trás disso é que vários bugs ocorrerem porque os objetos estão em um estado em que nunca deveriam ter ficado.</span><span class="sxs-lookup"><span data-stu-id="09326-112">The reasoning behind this is that many bugs occur because objects are in a state they should never have been in.</span></span> <span data-ttu-id="09326-113">A seguir está uma boa explicação de Greg Young em uma [discussão online](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span><span class="sxs-lookup"><span data-stu-id="09326-113">The following is a good explanation from Greg Young in an [online discussion](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span></span>

<span data-ttu-id="09326-114">Vamos propor que agora temos um SendUserCreationEmailService que usa um UserProfile..., como podemos racionalizar nesse serviço que o Nome não é nulo?</span><span class="sxs-lookup"><span data-stu-id="09326-114">Let's propose we now have a SendUserCreationEmailService that takes a UserProfile ... how can we rationalize in that service that Name is not null?</span></span> <span data-ttu-id="09326-115">Podemos verificar novamente?</span><span class="sxs-lookup"><span data-stu-id="09326-115">Do we check it again?</span></span> <span data-ttu-id="09326-116">Ou, mais provável… você apenas não se preocupa em verificar e "espera pelo melhor": você espera que alguém tenha se preocupado em validá-lo antes de enviá-lo a você.</span><span class="sxs-lookup"><span data-stu-id="09326-116">Or more likely ... you just don't bother to check and "hope for the best"—you hope that someone bothered to validate it before sending it to you.</span></span> <span data-ttu-id="09326-117">É claro que, usando TDD, um dos primeiros testes que devemos escrever é que, se eu enviar um cliente com um nome nulo, isso deverá gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="09326-117">Of course, using TDD one of the first tests we should be writing is that if I send a customer with a null name that it should raise an error.</span></span> <span data-ttu-id="09326-118">Porém, quando começarmos a escrever esses tipos de testes repetidamente, percebemos… "espere, se nunca tivéssemos permitido que o nome se tornasse nulo, não teríamos todos esses testes"</span><span class="sxs-lookup"><span data-stu-id="09326-118">But once we start writing these kinds of tests over and over again we realize ... "wait if we never allowed name to become null we wouldn't have all of these tests"</span></span>

## <a name="implementing-validations-in-the-domain-model-layer"></a><span data-ttu-id="09326-119">Implementando validações na camada de modelo de domínio</span><span class="sxs-lookup"><span data-stu-id="09326-119">Implementing validations in the domain model layer</span></span>

<span data-ttu-id="09326-120">As validações normalmente são implementadas em construtores de entidade de domínio ou em métodos que podem atualizar a entidade.</span><span class="sxs-lookup"><span data-stu-id="09326-120">Validations are usually implemented in domain entity constructors or in methods that can update the entity.</span></span> <span data-ttu-id="09326-121">Existem várias maneiras de implementar validações, como verificar dados e aumentar exceções se a validação falhar.</span><span class="sxs-lookup"><span data-stu-id="09326-121">There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails.</span></span> <span data-ttu-id="09326-122">Também há padrões mais avançados, como usar o padrão de Especificação para validações e o padrão de Notificação para retornar uma coleção de erros, em vez de retornar uma exceção para cada validação conforme ela ocorre.</span><span class="sxs-lookup"><span data-stu-id="09326-122">There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.</span></span>

### <a name="validating-conditions-and-throwing-exceptions"></a><span data-ttu-id="09326-123">Validando condições e gerando exceções</span><span class="sxs-lookup"><span data-stu-id="09326-123">Validating conditions and throwing exceptions</span></span>

<span data-ttu-id="09326-124">O exemplo de código a seguir mostra a abordagem mais simples de validação em uma entidade de domínio gerando uma exceção.</span><span class="sxs-lookup"><span data-stu-id="09326-124">The following code example shows the simplest approach to validation in a domain entity by raising an exception.</span></span> <span data-ttu-id="09326-125">Na tabela de referências no final desta seção, você encontrará links para implementações mais avançadas com base nos padrões que discutimos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="09326-125">In the references table at the end of this section you can see links to more advanced implementations based on the patterns we have discussed previously.</span></span>

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

<span data-ttu-id="09326-126">Um exemplo melhor seria demonstrar a necessidade de garantir que o estado interno não tenha mudado ou que todas as mutações para um método ocorreram.</span><span class="sxs-lookup"><span data-stu-id="09326-126">A better example would demonstrate the need to ensure that either the internal state did not change, or that all the mutations for a method occurred.</span></span> <span data-ttu-id="09326-127">Por exemplo, a implementação a seguir deixará o objeto em um estado inválido:</span><span class="sxs-lookup"><span data-stu-id="09326-127">For example, the following implementation would leave the object in an invalid state:</span></span>

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

<span data-ttu-id="09326-128">Se o valor do estado for inválido, a primeira linha de endereço e a cidade já terão sido alteradas.</span><span class="sxs-lookup"><span data-stu-id="09326-128">If the value of the state is invalid, the first address line and the city have already been changed.</span></span> <span data-ttu-id="09326-129">Isso pode tornar o endereço inválido.</span><span class="sxs-lookup"><span data-stu-id="09326-129">That might make the address invalid.</span></span>

<span data-ttu-id="09326-130">Uma abordagem semelhante pode ser usada no construtor da entidade, gerando uma exceção para garantir que a entidade seja válida quando for criada.</span><span class="sxs-lookup"><span data-stu-id="09326-130">A similar approach can be used in the entity’s constructor, raising an exception to make sure that the entity is valid once it is created.</span></span>

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a><span data-ttu-id="09326-131">Usando atributos de validação no modelo com base em anotações de dados</span><span class="sxs-lookup"><span data-stu-id="09326-131">Using validation attributes in the model based on data annotations</span></span>

<span data-ttu-id="09326-132">Outra abordagem é usar os atributos de validação com base em anotações de dados.</span><span class="sxs-lookup"><span data-stu-id="09326-132">Another approach is to use validation attributes based on data annotations.</span></span> <span data-ttu-id="09326-133">Os atributos de validação oferecem uma maneira de configurar a validação do modelo; isso é conceitualmente semelhante à validação em campos de tabelas de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="09326-133">Validation attributes provide a way to configure model validation, which is similar conceptually to validation on fields in database tables.</span></span> <span data-ttu-id="09326-134">Isso inclui restrições, como atribuição de tipos de dados ou campos obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="09326-134">This includes constraints such as assigning data types or required fields.</span></span> <span data-ttu-id="09326-135">Outros tipos de validação incluem a aplicação de padrões a dados para impor regras de negócio, como um número de cartão de crédito, número de telefone ou endereço de email.</span><span class="sxs-lookup"><span data-stu-id="09326-135">Other types of validation include applying patterns to data to enforce business rules, such as a credit card number, phone number, or email address.</span></span> <span data-ttu-id="09326-136">Atributos de validação tornam fácil impor os requisitos.</span><span class="sxs-lookup"><span data-stu-id="09326-136">Validation attributes make it easy to enforce requirements.</span></span>

<span data-ttu-id="09326-137">No entanto, conforme mostra o código a seguir, essa abordagem pode ser muito invasiva em um modelo DDD, porque tem uma dependência ModelState.IsValid de Microsoft.AspNetCore.Mvc.ModelState, que você deve chamar de seus controladores MVC.</span><span class="sxs-lookup"><span data-stu-id="09326-137">However, as shown in the following code, this approach might be too intrusive in a DDD model, because it takes a dependency on ModelState.IsValid from Microsoft.AspNetCore.Mvc.ModelState, which you must call from your MVC controllers.</span></span> <span data-ttu-id="09326-138">A validação do modelo ocorre antes de cada ação de controlador ser invocada, e é responsabilidade do método do controlador inspecionar o resultado da chamada ModelState.IsValid e reagir de maneira adequada.</span><span class="sxs-lookup"><span data-stu-id="09326-138">The model validation occurs prior to each controller action being invoked, and it is the controller method’s responsibility to inspect the result of calling ModelState.IsValid and react appropriately.</span></span> <span data-ttu-id="09326-139">A decisão de usá-lo depende de quão firmemente acoplado você deseja que o modelo esteja àquela infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="09326-139">The decision to use it depends on how tightly coupled you want the model to be with that infrastructure.</span></span>

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

<span data-ttu-id="09326-140">No entanto, de um ponto de vista de DDD, o modelo de domínio é mantido mais enxuto com o uso de exceções em seus métodos de comportamento da entidade ou implementando os padrões de Especificação e Notificação para impor regras de validação.</span><span class="sxs-lookup"><span data-stu-id="09326-140">However, from a DDD point of view, the domain model is best kept lean with the use of exceptions in your entity’s behavior methods, or by implementing the Specification and Notification patterns to enforce validation rules.</span></span> <span data-ttu-id="09326-141">Estruturas de validação como anotações de dados no ASP.NET Core ou quaisquer outras estruturas de validação, como FluentValidation, têm um requisito de invocar a estrutura do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="09326-141">Validation frameworks like data annotations in ASP.NET Core or any other validation frameworks like FluentValidation carry a requirement to invoke the application framework.</span></span> <span data-ttu-id="09326-142">Por exemplo, ao chamar o método ModelState.IsValid nas anotações de dados, você precisa invocar controladores do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="09326-142">For example, when calling the ModelState.IsValid method in data annotations, you need to invoke ASP.NET controllers.</span></span>

<span data-ttu-id="09326-143">Pode fazer sentido usar anotações de dados na camada de aplicativo em classes ViewModel (em vez de entidades de domínio) que aceitem a entrada para permitir a validação do modelo na camada da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="09326-143">It can make sense to use data annotations at the application layer in ViewModel classes (instead of domain entities) that will accept input, to allow for model validation within the UI layer.</span></span> <span data-ttu-id="09326-144">No entanto, isso não deve ser feito na exclusão de validação dentro do modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="09326-144">However, this should not be done at the exclusion of validation within the domain model.</span></span>

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a><span data-ttu-id="09326-145">Validando entidades implementando o padrão de Especificação e o padrão de Notificação</span><span class="sxs-lookup"><span data-stu-id="09326-145">Validating entities by implementing the Specification pattern and the Notification pattern</span></span>

<span data-ttu-id="09326-146">Por fim, uma abordagem mais elaborada para implementar a validação no modelo de domínio é implementando o padrão de Especificação em conjunto com o padrão de Notificação, conforme explicado em alguns dos recursos adicionais listados posteriormente.</span><span class="sxs-lookup"><span data-stu-id="09326-146">Finally, a more elaborate approach to implementing validations in the domain model is by implementing the Specification pattern in conjunction with the Notification pattern, as explained in some of the additional resources listed later.</span></span>

<span data-ttu-id="09326-147">Vale a pena mencionar que você também pode usar apenas um desses padrões — por exemplo, validação manual com instruções de controle, mas usando o padrão de Notificação para empilhar e retornar uma lista de erros de validação.</span><span class="sxs-lookup"><span data-stu-id="09326-147">It is worth mentioning that you can also use just one of those patterns—for example, validating manually with control statements, but using the Notification pattern to stack and return a list of validation errors.</span></span>

### <a name="using-deferred-validation-in-the-domain"></a><span data-ttu-id="09326-148">Usando a validação adiada no domínio</span><span class="sxs-lookup"><span data-stu-id="09326-148">Using deferred validation in the domain</span></span>

<span data-ttu-id="09326-149">Existem várias abordagens para lidar com validações adiadas no domínio.</span><span class="sxs-lookup"><span data-stu-id="09326-149">There are various approaches to deal with deferred validations in the domain.</span></span> <span data-ttu-id="09326-150">Em seu livro [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577) (Implementando design controlado por domínio), Vaughn Vernon discute isso na seção sobre a validação.</span><span class="sxs-lookup"><span data-stu-id="09326-150">In his book [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discusses these in the section on validation.</span></span>

### <a name="two-step-validation"></a><span data-ttu-id="09326-151">Validação de duas etapas</span><span class="sxs-lookup"><span data-stu-id="09326-151">Two-step validation</span></span>

<span data-ttu-id="09326-152">Considere também a validação de duas etapas.</span><span class="sxs-lookup"><span data-stu-id="09326-152">Also consider two-step validation.</span></span> <span data-ttu-id="09326-153">Use a validação em nível de campo em seu comando de DTOs (Objetos de Transferência de Dados) e a validação em nível de domínio dentro de suas entidades.</span><span class="sxs-lookup"><span data-stu-id="09326-153">Use field-level validation on your command Data Transfer Objects (DTOs) and domain-level validation inside your entities.</span></span> <span data-ttu-id="09326-154">Você pode fazer isso retornando um objeto de resultado em vez de exceções para tornar mais fácil lidar com os erros de validação.</span><span class="sxs-lookup"><span data-stu-id="09326-154">You can do this by returning a result object instead exceptions in order to make it easier to deal with the validation errors.</span></span>

<span data-ttu-id="09326-155">Usando a validação de campo com anotações de dados, por exemplo, você não duplica a definição de validação.</span><span class="sxs-lookup"><span data-stu-id="09326-155">Using field validation with data annotations, for example, you do not duplicate the validation definition.</span></span> <span data-ttu-id="09326-156">A execução, no entanto, pode estar do lado do servidor e do lado do cliente no caso de DTOs (comandos e ViewModels, por exemplo).</span><span class="sxs-lookup"><span data-stu-id="09326-156">The execution, though, can be both server-side and client-side in the case of DTOs (commands and ViewModels, for instance).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="09326-157">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="09326-157">Additional resources</span></span>

-   <span data-ttu-id="09326-158">**Rachel Appel. Introdução à validação do modelo no MVC do ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span><span class="sxs-lookup"><span data-stu-id="09326-158">**Rachel Appel. Introduction to model validation in ASP.NET Core MVC**
[*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span></span>

-   <span data-ttu-id="09326-159">**Rick Anderson. Adicionando validação**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="09326-159">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

-   <span data-ttu-id="09326-160">**Martin Fowler. Substituindo a geração de exceções por notificação em validações**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span><span class="sxs-lookup"><span data-stu-id="09326-160">**Martin Fowler. Replacing Throwing Exceptions with Notification in Validations**
[*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span></span>

-   <span data-ttu-id="09326-161">**Specification and Notification Patterns (Padrões de especificação e de notificação)**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span><span class="sxs-lookup"><span data-stu-id="09326-161">**Specification and Notification Patterns**
[*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span></span>

-   <span data-ttu-id="09326-162">**Lev Gorodinski. Validação em DDD (design controlado por domínio)**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span><span class="sxs-lookup"><span data-stu-id="09326-162">**Lev Gorodinski. Validation in Domain-Driven Design (DDD)**
[*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span></span>

-   <span data-ttu-id="09326-163">**Colin Jack. Validação de modelo de domínio**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span><span class="sxs-lookup"><span data-stu-id="09326-163">**Colin Jack. Domain Model Validation**
[*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span></span>

-   <span data-ttu-id="09326-164">**Jimmy Bogard. Validação em um mundo de DDD**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span><span class="sxs-lookup"><span data-stu-id="09326-164">**Jimmy Bogard. Validation in a DDD world**
[*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="09326-165">[Anterior] (enumeration-classes-over-enum-types.md) [Próximo] (client-side-validation.md)</span><span class="sxs-lookup"><span data-stu-id="09326-165">[Previous] (enumeration-classes-over-enum-types.md) [Next] (client-side-validation.md)</span></span>
