---
title: Implementando objetos de valor
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Implementando objetos de valor"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e6ac6f2d316a94e69c2599acf07aaaf6361b3e5a
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2018
---
# <a name="implementing-value-objects"></a><span data-ttu-id="9e5d3-104">Implementando objetos de valor</span><span class="sxs-lookup"><span data-stu-id="9e5d3-104">Implementing value objects</span></span>

<span data-ttu-id="9e5d3-105">Conforme discutido nas seções anteriores sobre entidades e agregações, a identidade é fundamental para entidades.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-105">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="9e5d3-106">No entanto, existem muitos objetos e itens de dados em um sistema que não exigem uma identidade e um acompanhamento de identidade, como objetos de valor.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-106">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="9e5d3-107">Um objeto de valor pode fazer referência a outras entidades.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-107">A value object can reference other entities.</span></span> <span data-ttu-id="9e5d3-108">Por exemplo, em um aplicativo que gera uma rota que descreve como ir de um ponto para outro, essa rota deve ser um objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-108">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="9e5d3-109">Seria um instantâneo de pontos em uma rota específica, mas essa rota sugerida não teria uma identidade, embora internamente possa fazer referência a entidades, como Cidade, Estrada etc.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-109">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="9e5d3-110">A Figura 9-13 mostra o objeto de valor Endereço dentro do agregado de Ordem.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-110">Figure 9-13 shows the Address value object within the Order aggregate.</span></span>

![](./media/image14.png)

<span data-ttu-id="9e5d3-111">**Figura 9-13**.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-111">**Figure 9-13**.</span></span> <span data-ttu-id="9e5d3-112">Tratar objeto de valor no agregado de Ordem</span><span class="sxs-lookup"><span data-stu-id="9e5d3-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="9e5d3-113">Conforme mostrado na Figura 9-13, uma entidade geralmente é composta por vários atributos.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-113">As shown in Figure 9-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="9e5d3-114">Por exemplo, a entidade `Order` pode ser modelada como uma entidade com uma identidade e composta internamente por um conjunto de atributos como OrderId, OrderDate, OrderItems etc. Mas o endereço, que é simplesmente um valor complexo composto por país, rua, cidade etc. e não tem nenhuma identidade nesse domínio, deve ser modelado e tratado como um objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex value composed of country, street, city, etc. and has no identity in this domain,  must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="9e5d3-115">Características importantes de objetos de valor</span><span class="sxs-lookup"><span data-stu-id="9e5d3-115">Important characteristics of value objects</span></span>

<span data-ttu-id="9e5d3-116">Existem duas características principais para objetos de valor:</span><span class="sxs-lookup"><span data-stu-id="9e5d3-116">There are two main characteristics for value objects:</span></span>

-   <span data-ttu-id="9e5d3-117">Eles não têm identidade.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-117">They have no identity.</span></span>

-   <span data-ttu-id="9e5d3-118">Eles são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-118">They are immutable.</span></span>

<span data-ttu-id="9e5d3-119">A primeira característica já foi discutida.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="9e5d3-120">A imutabilidade é um requisito importante.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-120">Immutability is an important requirement.</span></span> <span data-ttu-id="9e5d3-121">Os valores de um objeto de valor devem ser imutáveis depois que o objeto for criado.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="9e5d3-122">Portanto, quando o objeto é construído, você deve fornecer os valores necessários, mas não deve permitir que mudem durante o tempo de vida do objeto.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="9e5d3-123">Objetos de valor permitem que você execute certos truques para desempenho graças à sua natureza imutável.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="9e5d3-124">Isso é especialmente verdadeiro em sistemas em que pode haver milhares de instâncias de objeto de valor, muitas das quais com os mesmos valores.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="9e5d3-125">Sua natureza imutável permite que sejam reutilizados; eles podem ser objetos intercambiáveis, desde que seus valores sejam os mesmos e não tenham identidade.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="9e5d3-126">Esse tipo de otimização às vezes pode ser a diferença entre o software executado lentamente e o software com bom desempenho.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="9e5d3-127">Obviamente, todos esses casos dependem do ambiente do aplicativo e do contexto de implantação.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="9e5d3-128">Implementação de objeto de valor em C\#</span><span class="sxs-lookup"><span data-stu-id="9e5d3-128">Value object implementation in C\#</span></span>

<span data-ttu-id="9e5d3-129">Em termos de implementação, você pode ter uma classe base de objeto de valor que tenha métodos de utilitário básicos como igualdade com base na comparação entre todos os atributos (já que um objeto de valor não deve ser baseado em identidade) e outras características fundamentais.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="9e5d3-130">O exemplo a seguir mostra uma classe base do objeto de valor usada no microsserviço de ordenação de eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

```csharp
public abstract class ValueObject
{
    protected static bool EqualOperator(ValueObject left, ValueObject right)
    {
        if (ReferenceEquals(left, null) ^ ReferenceEquals(right, null))
        {
            return false;
        }
        return ReferenceEquals(left, null) || left.Equals(right);
    }

    protected static bool NotEqualOperator(ValueObject left, ValueObject right)
    {
        return !(EqualOperator(left, right));
    }

    protected abstract IEnumerable<object> GetAtomicValues();

    public override bool Equals(object obj)
    {
        if (obj == null || obj.GetType() != GetType())
        {
            return false;
        }

        ValueObject other = (ValueObject)obj;
        IEnumerator<object> thisValues = GetAtomicValues().GetEnumerator();
        IEnumerator<object> otherValues = other.GetAtomicValues().GetEnumerator();
        while (thisValues.MoveNext() && otherValues.MoveNext())
        {
            if (ReferenceEquals(thisValues.Current, null) ^
                ReferenceEquals(otherValues.Current, null))
            {
                return false;
            }

            if (thisValues.Current != null &&
                !thisValues.Current.Equals(otherValues.Current))
            {
                return false;
            }
        }
        return !thisValues.MoveNext() && !otherValues.MoveNext();
    }
    // Other utilility methods
}
```

<span data-ttu-id="9e5d3-131">Você pode usar essa classe durante a implementação do seu objeto de valor real, assim como acontece com o objeto de valor Endereço mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9e5d3-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

    private Address() { }

    public Address(string street, string city, string state, string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetAtomicValues()
    {
        // Using a yield return statement to return each element one at a time
        yield return Street;
        yield return City;
        yield return State;
        yield return Country;
        yield return ZipCode;
    }
}
```

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a><span data-ttu-id="9e5d3-132">Como manter objetos de valor no banco de dados com o EF Core 2.0</span><span class="sxs-lookup"><span data-stu-id="9e5d3-132">How to persist value objects in the database with EF Core 2.0</span></span>

<span data-ttu-id="9e5d3-133">Você acabou de ver como definir um objeto de valor em seu modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-133">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="9e5d3-134">Porém, como pode você realmente mantê-lo no banco de dados por meio de núcleo do EF (Entity Framework) que geralmente tem como alvo entidades com identidade?</span><span class="sxs-lookup"><span data-stu-id="9e5d3-134">But, how can you actually persist it into the database through Entity Framework (EF) Core which usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="9e5d3-135">Tela de fundo e abordagens mais antigas usando EF Core 1.1</span><span class="sxs-lookup"><span data-stu-id="9e5d3-135">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="9e5d3-136">Como contexto, uma limitação ao usar EF Core 1.0 e 1.1 era que você não podia usar [tipos complexos](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) conforme definido no EF 6. x no .NET Framework tradicional.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-136">As background, a limitation when using EF Core 1.0 and 1.1 was that you cannot use  [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="9e5d3-137">Portanto, se estiver usando EF Core 1.0 ou 1.1, precisará armazenar seu objeto de valor como uma entidade EF com um campo de ID.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-137">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="9e5d3-138">Então, para que se pareça mais com um objeto de valor sem nenhuma identidade, você pode ocultar a ID para deixar claro que a identidade de um objeto de valor não é importante no modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-138">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="9e5d3-139">Você pode ocultar essa ID usando a ID como um [propriedade de sombra](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span><span class="sxs-lookup"><span data-stu-id="9e5d3-139">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="9e5d3-140">Uma vez que a configuração para ocultar a ID do modelo é configurada no nível de infraestrutura do EF, seria transparente para o seu modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-140">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="9e5d3-141">Na versão inicial do eShopOnContainers (.NET Core 1.1), a ID oculta necessária para a infraestrutura do EF Core foi implementada da seguinte maneira no nível de DbContext, usando a API Fluente no projeto de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-141">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="9e5d3-142">Portanto, a ID foi oculta do ponto de vista do domínio modelo de domínio, mas ainda está na infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-142">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

```csharp
// Old approach with EF Core 1.1
// Fluent API within the OrderingContext:DbContext in the Infrastructure project
void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration) 
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA); 

    addressConfiguration.Property<int>("Id")  // Id is a shadow property
        .IsRequired();
    addressConfiguration.HasKey("Id");   // Id is a shadow property
}
```

<span data-ttu-id="9e5d3-143">No entanto, a persistência desse objeto de valor no banco de dados foi executada como uma entidade normal em uma tabela diferente.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-143">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="9e5d3-144">Com o EF Core 2.0, há maneiras novas e melhores de manter objetos de valor.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-144">With EF Core 2.0, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a><span data-ttu-id="9e5d3-145">Manter objetos de valor como tipos de entidade própria no EF Core 2.0</span><span class="sxs-lookup"><span data-stu-id="9e5d3-145">Persist value objects as owned entity types in EF Core 2.0</span></span>

<span data-ttu-id="9e5d3-146">Mesmo com algumas lacunas entre o padrão de objeto de valor canônico em DDD e o tipo de entidade de propriedade no EF Core, atualmente é a melhor maneira de manter objetos de valor com EF Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-146">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0.</span></span> <span data-ttu-id="9e5d3-147">Você pode ver as limitações no final desta seção.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-147">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="9e5d3-148">O recurso de tipo de entidade própria foi adicionado ao EF Core desde a versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-148">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="9e5d3-149">Um tipo de entidade própria permite mapear tipos que não têm a própria identidade definida explicitamente no modelo de domínio e são usados como propriedades, como um objeto de valor, em qualquer uma de suas entidades.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-149">An owned entity type allows you to map types that do not have their own identity explicitely defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="9e5d3-150">Um tipo de entidade própria compartilha o mesmo tipo CLR com outro tipo de entidade.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-150">An owned entity type shares the same CLR type with another entity type.</span></span> <span data-ttu-id="9e5d3-151">A entidade que contém a navegação de definição é a entidade proprietária.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-151">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="9e5d3-152">Ao consultar o proprietário, os tipos próprios serão incluídos por padrão.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-152">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="9e5d3-153">Apenas observando o modelo de domínio, um tipo de propriedade parece não ter identidade alguma.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-153">Just by looking at the domain model, an owned type looks like it doesn’t have any identity.</span></span>
<span data-ttu-id="9e5d3-154">No entanto, nos bastidores, tipos próprios têm identidade, mas a propriedade de navegação do proprietário faz parte dessa identidade.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-154">However, under the covers, owned types do have identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="9e5d3-155">A identidade de instâncias de tipos próprios não é completamente própria.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-155">The identity of instances of own types is not completely their own.</span></span> <span data-ttu-id="9e5d3-156">Consiste em três componentes:</span><span class="sxs-lookup"><span data-stu-id="9e5d3-156">It consists of three components:</span></span>

- <span data-ttu-id="9e5d3-157">A identidade do proprietário</span><span class="sxs-lookup"><span data-stu-id="9e5d3-157">The identity of the owner</span></span>

- <span data-ttu-id="9e5d3-158">A propriedade de navegação apontando para elas</span><span class="sxs-lookup"><span data-stu-id="9e5d3-158">The navigation property pointing to them</span></span>

- <span data-ttu-id="9e5d3-159">No caso de coleções de tipos próprios, um componente independente (ainda não compatível com o EF Core 2.0).</span><span class="sxs-lookup"><span data-stu-id="9e5d3-159">In the case of collections of owned types, an independent component (not yet supported in EF Core 2.0).</span></span>

<span data-ttu-id="9e5d3-160">Por exemplo, no modelo de domínio Ordenação em eShopOnContainers, como parte da entidade de Ordem, o objeto de valor de endereço é implementado como um tipo de entidade própria dentro da entidade de proprietário, que é a entidade Ordem.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-160">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="9e5d3-161">Endereço é um tipo sem propriedade de identidade definida no modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-161">Address is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="9e5d3-162">Ele é usado como uma propriedade do tipo Ordem para especificar o endereço para entrega para uma ordem específica.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-162">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="9e5d3-163">Por convenção, uma chave primária de sombra será criada para o tipo próprio e será mapeada para a mesma tabela que a do proprietário usando a divisão de tabela.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-163">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="9e5d3-164">Isso permite usar tipos próprios de modo similar a como os tipos complexos são usados no EF6 no .NET Framework tradicional.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-164">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="9e5d3-165">É importante observar que tipos próprios nunca são descobertos pela convenção no núcleo do EF, assim, você precisa declará-los explicitamente.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-165">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="9e5d3-166">Em eShopOnContainers, em OrderingContext.cs, no método OnModelCreating(), há várias configurações de infraestrutura que estão sendo aplicadas.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-166">In eShopOnContainers, at the OrderingContext.cs, within the OnModelCreating() method, there are multiple infrastructure configuration being applied.</span></span> <span data-ttu-id="9e5d3-167">Um deles está relacionado à entidade Ordem.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-167">One of them is related to the Order entity.</span></span>

```csharp
// Part of the OrderingContext.cs class at the Ordering.Infrastructure project
// 
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    modelBuilder.ApplyConfiguration(new ClientRequestEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new PaymentMethodEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new OrderItemEntityTypeConfiguration());
    //...Additional type configurations
}
```

<span data-ttu-id="9e5d3-168">No código a seguir, a infraestrutura de persistência é definida para a entidade Ordem:</span><span class="sxs-lookup"><span data-stu-id="9e5d3-168">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

```csharp
// Part of the OrderEntityTypeConfiguration.cs class 
// 
public void Configure(EntityTypeBuilder<Order> orderConfiguration)
{
    orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
    orderConfiguration.HasKey(o => o.Id);
    orderConfiguration.Ignore(b => b.DomainEvents);
    orderConfiguration.Property(o => o.Id)
        .ForSqlServerUseSequenceHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

    //Address value object persisted as owned entity in EF Core 2.0
    orderConfiguration.OwnsOne(o => o.Address);

    orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
    
    //...Additional validations, constraints and code...
    //...
}
```

<span data-ttu-id="9e5d3-169">No código anterior, o método `orderConfiguration.OwnsOne(o => o.Address)` especifica que a propriedade `Address` é uma entidade própria do tipo `Order`.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-169">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="9e5d3-170">Por padrão, as colunas de nome e banco de dados de convenções do EF Core para as propriedades do tipo de entidade própria como `EntityProperty_OwnedEntityProperty`.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-170">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="9e5d3-171">Portanto, as propriedades internas de `Address` aparecerão na tabela `Orders` com os nomes `Address_Street`, `Address_City` (e assim por diante para `State`, `Country` e `ZipCode`).</span><span class="sxs-lookup"><span data-stu-id="9e5d3-171">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country` and `ZipCode`).</span></span>

<span data-ttu-id="9e5d3-172">Você pode acrescentar o método fluente `Property().HasColumnName()` para renomear as colunas.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-172">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="9e5d3-173">No caso em que `Address` é uma propriedade pública, os mapeamentos seriam semelhantes ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="9e5d3-173">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="9e5d3-174">É possível encadear o método `OwnsOne` em um mapeamento fluente.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-174">It is possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="9e5d3-175">No exemplo hipotético a seguir, `OrderDetails` tem `BillingAddress` e `ShippingAddress`, que são tipos `Address`.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-175">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="9e5d3-176">Então `OrderDetails` pertence ao tipo `Order`.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-176">Then `OrderDetails` is owned by the `Order` type.</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.OrderDetails, cb =>
    {
        cb.OwnsOne(c => c.BillingAddress);
        cb.OwnsOne(c => c.ShippingAddress);
    });
//...
//...
public class Order
{
    public int Id { get; set; }
    public OrderDetails OrderDetails { get; set; }
}

public class OrderDetails
{
    public Address BillingAddress { get; set; }
    public Address ShippingAddress { get; set; }
}

public class Address
{
    public string Street { get; set; }
    public string City { get; set; }
}
```

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="9e5d3-177">Detalhes adicionais sobre tipos de entidade própria</span><span class="sxs-lookup"><span data-stu-id="9e5d3-177">Additional details on owned entity types</span></span>

<span data-ttu-id="9e5d3-178">• Tipos próprios são definidos quando você configura uma propriedade de navegação para um tipo específico usando a API fluente OwnsOne.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-178">•   Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

<span data-ttu-id="9e5d3-179">• A definição de um tipo próprio em nosso modelo de metadados é uma composição de: tipo de proprietário, a propriedade de navegação e o tipo CLR do tipo próprio.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-179">•   The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

<span data-ttu-id="9e5d3-180">• A identidade (chave) de uma instância de tipo próprio na nossa pilha é uma composição de identidade do tipo de proprietário e definição do tipo próprio.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-180">•   The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="9e5d3-181">Recursos de entidades próprias:</span><span class="sxs-lookup"><span data-stu-id="9e5d3-181">Owned entities capabilities:</span></span>

<span data-ttu-id="9e5d3-182">• O tipo próprio pode fazer referência a outras entidades, tanto próprias (tipos próprios aninhados) quanto não próprias (propriedades de navegação de referência comum para outras entidades).</span><span class="sxs-lookup"><span data-stu-id="9e5d3-182">•   Owned type can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

<span data-ttu-id="9e5d3-183">• Você pode mapear o mesmo tipo CLR como diferentes tipos próprios na mesma entidade de proprietário por meio das propriedades de navegação separadas.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-183">•   You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

<span data-ttu-id="9e5d3-184">• A divisão de tabela está configurada por convenção, mas você pode optar por não mapear o tipo próprio para uma tabela diferente usando ToTable.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-184">•   Table splitting is setup by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

<span data-ttu-id="9e5d3-185">• Carregamento adiantado é executado automaticamente em tipos próprios, ou seja, não há necessidade de chamar Include() na consulta.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-185">•   Eager loading is performed automatically on owned types, i.e. no need to call Include() on the query.</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="9e5d3-186">Limitações de entidades próprias:</span><span class="sxs-lookup"><span data-stu-id="9e5d3-186">Owned entities limitations:</span></span>

<span data-ttu-id="9e5d3-187">• Não é possível criar um DbSet<T> de um tipo próprio (por design).</span><span class="sxs-lookup"><span data-stu-id="9e5d3-187">•   You cannot create a DbSet<T> of an owned type (by design).</span></span>

<span data-ttu-id="9e5d3-188">• Você não pode chamar ModelBuilder.Entity<T>() em tipos próprios (atualmente por design).</span><span class="sxs-lookup"><span data-stu-id="9e5d3-188">•   You cannot call ModelBuilder.Entity<T>() on owned types (currently by design).</span></span>

<span data-ttu-id="9e5d3-189">• Nenhuma coleção de tipos próprios ainda (mas serão compatíveis com versões após EF Core 2.0).</span><span class="sxs-lookup"><span data-stu-id="9e5d3-189">•   No collections of owned types yet (but they will be supported in versions after EF Core 2.0).</span></span>

<span data-ttu-id="9e5d3-190">• Não há suporte para configurá-los por meio de um atributo.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-190">•   No support for configuring them via an attribute.</span></span>

<span data-ttu-id="9e5d3-191">• Não há suporte para tipos próprios opcionais (ou seja, anuláveis) mapeados com o proprietário da mesma tabela (ou seja, usando a divisão de tabela).</span><span class="sxs-lookup"><span data-stu-id="9e5d3-191">•   No support for optional (i.e. nullable) owned types that are mapped with the owner in the same table (i.e. using table splitting).</span></span> <span data-ttu-id="9e5d3-192">Isso ocorre porque não há um sentinela separado para o nulo.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-192">This is because we don't have a separate sentinel for the null.</span></span>

<span data-ttu-id="9e5d3-193">• Não há suporte de mapeamento de herança para tipos de propriedade, mas você deve ser capaz de mapear dois tipos de folha das mesmas hierarquias de herança como diferentes tipos próprios.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-193">•   No inheritance mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="9e5d3-194">O EF Core não argumentará sobre o fato de que fazem parte da mesma hierarquia.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-194">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="9e5d3-195">Principais diferenças com tipos complexos do EF6</span><span class="sxs-lookup"><span data-stu-id="9e5d3-195">Main differences with EF6's complex types</span></span>

<span data-ttu-id="9e5d3-196">• A divisão de tabela é opcional, ou seja, podem opcionalmente ser mapeados para uma tabela separada e ainda serem tipos próprios.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-196">•   Table splitting is optional, i.e. they can optionally be mapped to a separate table and still be owned types.</span></span>

<span data-ttu-id="9e5d3-197">• Podem fazer referência a outras entidades (ou seja, podem atuar como o lado dependente em relações com outros tipos não próprios).</span><span class="sxs-lookup"><span data-stu-id="9e5d3-197">•   They can reference other entities (i.e. they can act as the dependent side on relationships to other non-owned types).</span></span>


## <a name="additional-resources"></a><span data-ttu-id="9e5d3-198">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="9e5d3-198">Additional resources</span></span>

-   <span data-ttu-id="9e5d3-199">**Martin Fowler. Padrão ValueObject**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span><span class="sxs-lookup"><span data-stu-id="9e5d3-199">**Martin Fowler. ValueObject pattern**
[*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span></span>

-   <span data-ttu-id="9e5d3-200">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software (Design orientado por domínio: lidando com a complexidade no núcleo do software).**</span><span class="sxs-lookup"><span data-stu-id="9e5d3-200">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="9e5d3-201">(Livro; inclui uma discussão sobre os objetos de valor) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="9e5d3-201">(Book; includes a discussion of value objects) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="9e5d3-202">**Vaughn Vernon. Implementando um design conduzido por domínio.**</span><span class="sxs-lookup"><span data-stu-id="9e5d3-202">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="9e5d3-203">(Livro; inclui uma discussão sobre objetos de valor) [ *https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="9e5d3-203">(Book; includes a discussion of value objects) [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="9e5d3-204">**Propriedades de sombra**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="9e5d3-204">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>

-   <span data-ttu-id="9e5d3-205">**Tipos complexos e/ou objetos de valor**.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-205">**Complex types and/or value objects**.</span></span> <span data-ttu-id="9e5d3-206">Discussão no repositório GitHub do EF Core (guia Problemas) [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span><span class="sxs-lookup"><span data-stu-id="9e5d3-206">Discussion in the EF Core GitHub repo (Issues tab) [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span></span>

-   <span data-ttu-id="9e5d3-207">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="9e5d3-207">**ValueObject.cs.**</span></span> <span data-ttu-id="9e5d3-208">Classe de objeto de valor base no eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-208">Base value object class in eShopOnContainers.</span></span>
    [<span data-ttu-id="9e5d3-209">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*</span><span class="sxs-lookup"><span data-stu-id="9e5d3-209">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   <span data-ttu-id="9e5d3-210">**Classe de endereços.**</span><span class="sxs-lookup"><span data-stu-id="9e5d3-210">**Address class.**</span></span> <span data-ttu-id="9e5d3-211">Exemplo de classe de objeto de valor em eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="9e5d3-211">Sample value object class in eShopOnContainers.</span></span>
    [<span data-ttu-id="9e5d3-212">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*</span><span class="sxs-lookup"><span data-stu-id="9e5d3-212">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)



>[!div class="step-by-step"]
<span data-ttu-id="9e5d3-213">[Anterior] (seedwork-domain-model-base-classes-interfaces.md) [Próximo] (enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="9e5d3-213">[Previous] (seedwork-domain-model-base-classes-interfaces.md) [Next] (enumeration-classes-over-enum-types.md)</span></span>
