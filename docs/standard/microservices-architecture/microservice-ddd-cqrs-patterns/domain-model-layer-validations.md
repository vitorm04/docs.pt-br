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
# <a name="designing-validations-in-the-domain-model-layer"></a><span data-ttu-id="d6163-104">Criando validações na camada de modelo de domínio</span><span class="sxs-lookup"><span data-stu-id="d6163-104">Designing validations in the domain model layer</span></span>

<span data-ttu-id="d6163-105">No DDD, as regras de validação podem ser consideradas como invariáveis.</span><span class="sxs-lookup"><span data-stu-id="d6163-105">In DDD, validation rules can be thought as invariants.</span></span> <span data-ttu-id="d6163-106">A principal responsabilidade de uma agregação é impor invariáveis entre as alterações de estado para todas as entidades que agregam.</span><span class="sxs-lookup"><span data-stu-id="d6163-106">The main responsibility of an aggregate is to enforce invariants across state changes for all the entities within that aggregate.</span></span>

<span data-ttu-id="d6163-107">Entidades de domínio devem ser sempre entidades válidas.</span><span class="sxs-lookup"><span data-stu-id="d6163-107">Domain entities should always be valid entities.</span></span> <span data-ttu-id="d6163-108">Há um determinado número de constantes para um objeto que deve ser verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="d6163-108">There are a certain number of invariants for an object that should always be true.</span></span> <span data-ttu-id="d6163-109">Por exemplo, um objeto de item do pedido sempre deve ter uma quantidade que deve ser um inteiro positivo, além de um nome de artigo e o preço.</span><span class="sxs-lookup"><span data-stu-id="d6163-109">For example, an order item object always has to have a quantity that must be a positive integer, plus an article name and price.</span></span> <span data-ttu-id="d6163-110">Portanto, a imposição de invariáveis é de responsabilidade das entidades de domínio (especialmente da agregação raiz) e um objeto de entidade não deve ser capaz de existir sem que sejam válidos.</span><span class="sxs-lookup"><span data-stu-id="d6163-110">Therefore, invariants enforcement is the responsibility of the domain entities (especially of the aggregate root) and an entity object should not be able to exist without being valid.</span></span> <span data-ttu-id="d6163-111">Regras invariáveis simplesmente são expressos como contratos e exceções ou notificações são geradas quando eles forem violados.</span><span class="sxs-lookup"><span data-stu-id="d6163-111">Invariant rules are simply expressed as contracts, and exceptions or notifications are raised when they are violated.</span></span>

<span data-ttu-id="d6163-112">O raciocínio por trás disso é que vários bugs ocorrerem porque os objetos em um estado nunca deveria ter sido incluído.</span><span class="sxs-lookup"><span data-stu-id="d6163-112">The reasoning behind this is that many bugs occur because objects are in a state they should never have been in.</span></span> <span data-ttu-id="d6163-113">Esta é uma boa explicação de Greg Young em um [discussão on-line](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span><span class="sxs-lookup"><span data-stu-id="d6163-113">The following is a good explanation from Greg Young in an [online discussion](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span></span>

<span data-ttu-id="d6163-114">Vamos propor que agora temos uma SendUserCreationEmailService que leva a um perfil de usuário... como pode é racionalizar no serviço que o nome não é nulo?</span><span class="sxs-lookup"><span data-stu-id="d6163-114">Let's propose we now have a SendUserCreationEmailService that takes a UserProfile ... how can we rationalize in that service that Name is not null?</span></span> <span data-ttu-id="d6163-115">Podemos check-novamente?</span><span class="sxs-lookup"><span data-stu-id="d6163-115">Do we check it again?</span></span> <span data-ttu-id="d6163-116">Ou mais provável... você apenas não se preocupe para verificar e "esperar o melhor" — você espera que alguém se preocupou em validá-lo antes de enviá-lo para você.</span><span class="sxs-lookup"><span data-stu-id="d6163-116">Or more likely ... you just don't bother to check and "hope for the best"—you hope that someone bothered to validate it before sending it to you.</span></span> <span data-ttu-id="d6163-117">É claro que, usando TDD dos testes primeiro, deve gravar é que, se enviar um cliente com um nome nulo que deve gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="d6163-117">Of course, using TDD one of the first tests we should be writing is that if I send a customer with a null name that it should raise an error.</span></span> <span data-ttu-id="d6163-118">Mas, quando começarmos a gravar esses tipos de testes repetidamente sabemos... "aguardar se podemos nunca nome seja nulo não temos todos esses testes"</span><span class="sxs-lookup"><span data-stu-id="d6163-118">But once we start writing these kinds of tests over and over again we realize ... "wait if we never allowed name to become null we wouldn't have all of these tests"</span></span>

## <a name="implementing-validations-in-the-domain-model-layer"></a><span data-ttu-id="d6163-119">Implementando validações na camada de modelo de domínio</span><span class="sxs-lookup"><span data-stu-id="d6163-119">Implementing validations in the domain model layer</span></span>

<span data-ttu-id="d6163-120">Validações são normalmente implementadas em construtores de entidade de domínio ou em métodos que podem atualizar a entidade.</span><span class="sxs-lookup"><span data-stu-id="d6163-120">Validations are usually implemented in domain entity constructors or in methods that can update the entity.</span></span> <span data-ttu-id="d6163-121">Há várias maneiras de implementar validações, como verificação de dados e aumentando exceções se a validação falhar.</span><span class="sxs-lookup"><span data-stu-id="d6163-121">There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails.</span></span> <span data-ttu-id="d6163-122">Também há padrões mais avançados, como usando o padrão de especificação para validações e o padrão de notificação para retornar uma coleção de erros em vez de retornar uma exceção para cada validação conforme ela ocorre.</span><span class="sxs-lookup"><span data-stu-id="d6163-122">There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.</span></span>

### <a name="validating-conditions-and-throwing-exceptions"></a><span data-ttu-id="d6163-123">Validando condições e lançando exceções</span><span class="sxs-lookup"><span data-stu-id="d6163-123">Validating conditions and throwing exceptions</span></span>

<span data-ttu-id="d6163-124">O exemplo de código a seguir mostra a abordagem mais simples de validação em uma entidade de domínio, gerando uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d6163-124">The following code example shows the simplest approach to validation in a domain entity by raising an exception.</span></span> <span data-ttu-id="d6163-125">A tabela de referências no final desta seção, você encontrará links para implementações mais avançadas com base em padrões que discutimos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d6163-125">In the references table at the end of this section you can see links to more advanced implementations based on the patterns we have discussed previously.</span></span>

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

<span data-ttu-id="d6163-126">Um exemplo melhor seria demonstram a necessidade de garantir que o estado interno não foi alterado ou que todas as mutações para um método ocorreram.</span><span class="sxs-lookup"><span data-stu-id="d6163-126">A better example would demonstrate the need to ensure that either the internal state did not change, or that all the mutations for a method occurred.</span></span> <span data-ttu-id="d6163-127">Por exemplo, a seguinte implementação deixará o objeto em um estado inválido:</span><span class="sxs-lookup"><span data-stu-id="d6163-127">For example, the following implementation would leave the object in an invalid state:</span></span>

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

<span data-ttu-id="d6163-128">Se o valor do estado é inválido, a primeira linha de endereço e cidade já tem sido alterados.</span><span class="sxs-lookup"><span data-stu-id="d6163-128">If the value of the state is invalid, the first address line and the city have already been changed.</span></span> <span data-ttu-id="d6163-129">Que pode tornar o endereço inválido.</span><span class="sxs-lookup"><span data-stu-id="d6163-129">That might make the address invalid.</span></span>

<span data-ttu-id="d6163-130">Uma abordagem semelhante pode ser usada no construtor da entidade, gerando uma exceção para certificar-se de que a entidade é válido quando ele é criado.</span><span class="sxs-lookup"><span data-stu-id="d6163-130">A similar approach can be used in the entity’s constructor, raising an exception to make sure that the entity is valid once it is created.</span></span>

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a><span data-ttu-id="d6163-131">Usando atributos de validação no modelo com base em anotações de dados</span><span class="sxs-lookup"><span data-stu-id="d6163-131">Using validation attributes in the model based on data annotations</span></span>

<span data-ttu-id="d6163-132">Outra abordagem é usar os atributos de validação com base em anotações de dados.</span><span class="sxs-lookup"><span data-stu-id="d6163-132">Another approach is to use validation attributes based on data annotations.</span></span> <span data-ttu-id="d6163-133">Atributos de validação fornecem uma maneira de configurar a validação do modelo, que é semelhante conceitualmente a validação em campos em tabelas de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="d6163-133">Validation attributes provide a way to configure model validation, which is similar conceptually to validation on fields in database tables.</span></span> <span data-ttu-id="d6163-134">Isso inclui as restrições, como a atribuição de tipos de dados ou os campos obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="d6163-134">This includes constraints such as assigning data types or required fields.</span></span> <span data-ttu-id="d6163-135">Outros tipos de validação incluem a aplicação de padrões de dados para impor regras de negócio, como um número de cartão de crédito, número de telefone ou endereço de email.</span><span class="sxs-lookup"><span data-stu-id="d6163-135">Other types of validation include applying patterns to data to enforce business rules, such as a credit card number, phone number, or email address.</span></span> <span data-ttu-id="d6163-136">Atributos de validação tornam mais fácil aplicar os requisitos.</span><span class="sxs-lookup"><span data-stu-id="d6163-136">Validation attributes make it easy to enforce requirements.</span></span>

<span data-ttu-id="d6163-137">No entanto, conforme mostrado no código a seguir, essa abordagem pode ser muito intrusiva em um modelo DDD, porque ele tem uma dependência ModelState de Microsoft.AspNetCore.Mvc.ModelState, que deve ser chamado de seus controladores MVC.</span><span class="sxs-lookup"><span data-stu-id="d6163-137">However, as shown in the following code, this approach might be too intrusive in a DDD model, because it takes a dependency on ModelState.IsValid from Microsoft.AspNetCore.Mvc.ModelState, which you must call from your MVC controllers.</span></span> <span data-ttu-id="d6163-138">Ocorre a validação do modelo antes de cada ação de controlador que está sendo invocada, e é responsabilidade do método do controlador para inspecionar o resultado da chamada ModelState e reagir de forma adequada.</span><span class="sxs-lookup"><span data-stu-id="d6163-138">The model validation occurs prior to each controller action being invoked, and it is the controller method’s responsibility to inspect the result of calling ModelState.IsValid and react appropriately.</span></span> <span data-ttu-id="d6163-139">A decisão de usá-lo depende de como acoplado você quer que o modelo com que a infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="d6163-139">The decision to use it depends on how tightly coupled you want the model to be with that infrastructure.</span></span>

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

<span data-ttu-id="d6163-140">No entanto, de um ponto de vista DDD, o modelo de domínio é melhor mantido lean com o uso de exceções em métodos de comportamento da entidade ou por implementar os padrões de notificação e especificações para impor regras de validação.</span><span class="sxs-lookup"><span data-stu-id="d6163-140">However, from a DDD point of view, the domain model is best kept lean with the use of exceptions in your entity’s behavior methods, or by implementing the Specification and Notification patterns to enforce validation rules.</span></span> <span data-ttu-id="d6163-141">Estruturas de validação como anotações de dados no ASP.NET Core ou quaisquer outras estruturas de validação como FluentValidation realizar um requisito para invocar a estrutura de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d6163-141">Validation frameworks like data annotations in ASP.NET Core or any other validation frameworks like FluentValidation carry a requirement to invoke the application framework.</span></span> <span data-ttu-id="d6163-142">Por exemplo, ao chamar o método ModelState nas anotações de dados, você precisa chamar controladores do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d6163-142">For example, when calling the ModelState.IsValid method in data annotations, you need to invoke ASP.NET controllers.</span></span>

<span data-ttu-id="d6163-143">Ele pode fazer sentido usar anotações de dados na camada de aplicativo em classes ViewModel (em vez de entidades de domínio) que aceita a entrada, para permitir a validação do modelo dentro da camada de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="d6163-143">It can make sense to use data annotations at the application layer in ViewModel classes (instead of domain entities) that will accept input, to allow for model validation within the UI layer.</span></span> <span data-ttu-id="d6163-144">No entanto, isso não deve ser feito na exclusão de validação dentro do modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="d6163-144">However, this should not be done at the exclusion of validation within the domain model.</span></span>

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a><span data-ttu-id="d6163-145">Validando entidades Implementando o padrão de especificação e o padrão de notificação</span><span class="sxs-lookup"><span data-stu-id="d6163-145">Validating entities by implementing the Specification pattern and the Notification pattern</span></span>

<span data-ttu-id="d6163-146">Por fim, uma abordagem mais elaborada para implementar a validação no modelo de domínio está implementando o padrão de especificação em conjunto com o padrão de notificação, conforme explicado em alguns dos recursos adicionais listados posteriormente.</span><span class="sxs-lookup"><span data-stu-id="d6163-146">Finally, a more elaborate approach to implementing validations in the domain model is by implementing the Specification pattern in conjunction with the Notification pattern, as explained in some of the additional resources listed later.</span></span>

<span data-ttu-id="d6163-147">Vale a pena mencionar que você também pode usar apenas um desses padrões — por exemplo, validação manual com instruções de controle, mas usando o padrão de notificação de pilha e retornar uma lista de erros de validação.</span><span class="sxs-lookup"><span data-stu-id="d6163-147">It is worth mentioning that you can also use just one of those patterns—for example, validating manually with control statements, but using the Notification pattern to stack and return a list of validation errors.</span></span>

### <a name="using-deferred-validation-in-the-domain"></a><span data-ttu-id="d6163-148">Usando a validação adiada no domínio</span><span class="sxs-lookup"><span data-stu-id="d6163-148">Using deferred validation in the domain</span></span>

<span data-ttu-id="d6163-149">Há várias abordagens para lidar com validações adiadas no domínio.</span><span class="sxs-lookup"><span data-stu-id="d6163-149">There are various approaches to deal with deferred validations in the domain.</span></span> <span data-ttu-id="d6163-150">Em seu livro [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discute os na seção sobre a validação.</span><span class="sxs-lookup"><span data-stu-id="d6163-150">In his book [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discusses these in the section on validation.</span></span>

### <a name="two-step-validation"></a><span data-ttu-id="d6163-151">Validação de duas etapas</span><span class="sxs-lookup"><span data-stu-id="d6163-151">Two-step validation</span></span>

<span data-ttu-id="d6163-152">Considere também a validação de duas etapas.</span><span class="sxs-lookup"><span data-stu-id="d6163-152">Also consider two-step validation.</span></span> <span data-ttu-id="d6163-153">Use a validação de nível de campo em seu comando dados transferidos DTOs (objetos) e a validação de nível de domínio dentro de suas entidades.</span><span class="sxs-lookup"><span data-stu-id="d6163-153">Use field-level validation on your command Data Transfer Objects (DTOs) and domain-level validation inside your entities.</span></span> <span data-ttu-id="d6163-154">Você pode fazer isso, retornando um objeto de resultado em vez disso, exceções para tornar mais fácil de lidar com os erros de validação.</span><span class="sxs-lookup"><span data-stu-id="d6163-154">You can do this by returning a result object instead exceptions in order to make it easier to deal with the validation errors.</span></span>

<span data-ttu-id="d6163-155">Usando a validação de campo com anotações de dados, por exemplo, você não duplicar a definição de validação.</span><span class="sxs-lookup"><span data-stu-id="d6163-155">Using field validation with data annotations, for example, you do not duplicate the validation definition.</span></span> <span data-ttu-id="d6163-156">A execução, no entanto, pode ser do lado do servidor e cliente no caso de DTOs (comandos e ViewModels, por exemplo).</span><span class="sxs-lookup"><span data-stu-id="d6163-156">The execution, though, can be both server-side and client-side in the case of DTOs (commands and ViewModels, for instance).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d6163-157">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="d6163-157">Additional resources</span></span>

-   <span data-ttu-id="d6163-158">**Rachel Appel. Introdução à validação do modelo no MVC do ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span><span class="sxs-lookup"><span data-stu-id="d6163-158">**Rachel Appel. Introduction to model validation in ASP.NET Core MVC**
[*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span></span>

-   <span data-ttu-id="d6163-159">**Rick Anderson. Adicionando validação**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="d6163-159">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

-   <span data-ttu-id="d6163-160">**Martin Fowler. Substituindo Lançando exceções com notificação em validações**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span><span class="sxs-lookup"><span data-stu-id="d6163-160">**Martin Fowler. Replacing Throwing Exceptions with Notification in Validations**
[*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span></span>

-   <span data-ttu-id="d6163-161">**Especificação e padrões de notificação**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span><span class="sxs-lookup"><span data-stu-id="d6163-161">**Specification and Notification Patterns**
[*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span></span>

-   <span data-ttu-id="d6163-162">**Lev Gorodinski. Validação no Design orientado a domínio (DDD)**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span><span class="sxs-lookup"><span data-stu-id="d6163-162">**Lev Gorodinski. Validation in Domain-Driven Design (DDD)**
[*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span></span>

-   <span data-ttu-id="d6163-163">**Colin tomada. Validação de modelo de domínio**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span><span class="sxs-lookup"><span data-stu-id="d6163-163">**Colin Jack. Domain Model Validation**
[*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span></span>

-   <span data-ttu-id="d6163-164">**Jimmy Bogard. Validação em um mundo DDD**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span><span class="sxs-lookup"><span data-stu-id="d6163-164">**Jimmy Bogard. Validation in a DDD world**
[*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="d6163-165">[Anterior] (enumeração-classes-over-enum-types.md) [Avançar] (validation.md do lado do cliente)</span><span class="sxs-lookup"><span data-stu-id="d6163-165">[Previous] (enumeration-classes-over-enum-types.md) [Next] (client-side-validation.md)</span></span>
