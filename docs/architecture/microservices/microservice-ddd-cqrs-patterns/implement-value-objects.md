---
title: Implementando objetos de valor
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Obtenha os detalhes e as opções para implementar objetos de valor usando as novas funcionalidades do Entity Framework.
ms.date: 08/21/2020
ms.openlocfilehash: 02eed7baaa364c62aa2df599f1d8b0e700dd215f
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811113"
---
# <a name="implement-value-objects"></a><span data-ttu-id="ede59-103">Implementar objetos de valor</span><span class="sxs-lookup"><span data-stu-id="ede59-103">Implement value objects</span></span>

<span data-ttu-id="ede59-104">Conforme discutido nas seções anteriores sobre entidades e agregações, a identidade é fundamental para entidades.</span><span class="sxs-lookup"><span data-stu-id="ede59-104">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="ede59-105">No entanto, existem muitos objetos e itens de dados em um sistema que não exigem uma identidade e um acompanhamento de identidade, como objetos de valor.</span><span class="sxs-lookup"><span data-stu-id="ede59-105">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="ede59-106">Um objeto de valor pode fazer referência a outras entidades.</span><span class="sxs-lookup"><span data-stu-id="ede59-106">A value object can reference other entities.</span></span> <span data-ttu-id="ede59-107">Por exemplo, em um aplicativo que gera uma rota que descreve como ir de um ponto para outro, essa rota deve ser um objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="ede59-107">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="ede59-108">Seria um instantâneo de pontos em uma rota específica, mas essa rota sugerida não teria uma identidade, embora internamente possa fazer referência a entidades, como Cidade, Estrada etc.</span><span class="sxs-lookup"><span data-stu-id="ede59-108">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="ede59-109">A Figura 7-13 mostra o objeto de valor Endereço dentro da agregação Ordem.</span><span class="sxs-lookup"><span data-stu-id="ede59-109">Figure 7-13 shows the Address value object within the Order aggregate.</span></span>

![Diagrama que mostra o valor de endereço-objeto dentro da agregação de ordem.](./media/implement-value-objects/value-object-within-aggregate.png)

<span data-ttu-id="ede59-111">**Figura 7-13**.</span><span class="sxs-lookup"><span data-stu-id="ede59-111">**Figure 7-13**.</span></span> <span data-ttu-id="ede59-112">Tratar objeto de valor no agregado de Ordem</span><span class="sxs-lookup"><span data-stu-id="ede59-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="ede59-113">Conforme mostrado na Figura 7-13, uma entidade geralmente é composta por vários atributos.</span><span class="sxs-lookup"><span data-stu-id="ede59-113">As shown in Figure 7-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="ede59-114">Por exemplo, a `Order` entidade pode ser modelada como uma entidade com uma identidade e composta internamente por um conjunto de atributos, como OrderID, OrderDate, OrderItems, etc. Mas o endereço, que é simplesmente um valor complexo composto de país/região, rua, cidade etc. e não tem nenhuma identidade nesse domínio, deve ser modelado e tratado como um objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="ede59-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex-value composed of country/region, street, city, etc. and has no identity in this domain, must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="ede59-115">Características importantes de objetos de valor</span><span class="sxs-lookup"><span data-stu-id="ede59-115">Important characteristics of value objects</span></span>

<span data-ttu-id="ede59-116">Existem duas características principais para objetos de valor:</span><span class="sxs-lookup"><span data-stu-id="ede59-116">There are two main characteristics for value objects:</span></span>

- <span data-ttu-id="ede59-117">Eles não têm identidade.</span><span class="sxs-lookup"><span data-stu-id="ede59-117">They have no identity.</span></span>

- <span data-ttu-id="ede59-118">Eles são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="ede59-118">They are immutable.</span></span>

<span data-ttu-id="ede59-119">A primeira característica já foi discutida.</span><span class="sxs-lookup"><span data-stu-id="ede59-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="ede59-120">A imutabilidade é um requisito importante.</span><span class="sxs-lookup"><span data-stu-id="ede59-120">Immutability is an important requirement.</span></span> <span data-ttu-id="ede59-121">Os valores de um objeto de valor devem ser imutáveis depois que o objeto for criado.</span><span class="sxs-lookup"><span data-stu-id="ede59-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="ede59-122">Portanto, quando o objeto é construído, você deve fornecer os valores necessários, mas não deve permitir que eles sejam alterados durante o tempo de vida do objeto.</span><span class="sxs-lookup"><span data-stu-id="ede59-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object's lifetime.</span></span>

<span data-ttu-id="ede59-123">Objetos de valor permitem que você execute certos truques para desempenho graças à sua natureza imutável.</span><span class="sxs-lookup"><span data-stu-id="ede59-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="ede59-124">Isso é especialmente verdadeiro em sistemas em que pode haver milhares de instâncias de objeto de valor, muitas das quais com os mesmos valores.</span><span class="sxs-lookup"><span data-stu-id="ede59-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="ede59-125">Sua natureza imutável permite que sejam reutilizados; eles podem ser objetos intercambiáveis, desde que seus valores sejam os mesmos e não tenham identidade.</span><span class="sxs-lookup"><span data-stu-id="ede59-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="ede59-126">Esse tipo de otimização às vezes pode ser a diferença entre o software executado lentamente e o software com bom desempenho.</span><span class="sxs-lookup"><span data-stu-id="ede59-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="ede59-127">Obviamente, todos esses casos dependem do ambiente do aplicativo e do contexto de implantação.</span><span class="sxs-lookup"><span data-stu-id="ede59-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="ede59-128">Implementação de objeto de valor em C\#</span><span class="sxs-lookup"><span data-stu-id="ede59-128">Value object implementation in C\#</span></span>

<span data-ttu-id="ede59-129">Em termos de implementação, você pode ter uma classe base de objeto de valor que tenha métodos de utilitário básicos como igualdade com base na comparação entre todos os atributos (já que um objeto de valor não deve ser baseado em identidade) e outras características fundamentais.</span><span class="sxs-lookup"><span data-stu-id="ede59-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on the comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="ede59-130">O exemplo a seguir mostra uma classe base do objeto de valor usada no microsserviço de ordenação de eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="ede59-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

    protected abstract IEnumerable<object> GetEqualityComponents();

    public override bool Equals(object obj)
    {
        if (obj == null || obj.GetType() != GetType())
        {
            return false;
        }

        var other = (ValueObject)obj;

        return this.GetEqualityComponents().SequenceEqual(other.GetEqualityComponents());
    }

    public override int GetHashCode()
    {
        return GetEqualityComponents()
            .Select(x => x != null ? x.GetHashCode() : 0)
            .Aggregate((x, y) => x ^ y);
    }
    // Other utility methods
}
```

<span data-ttu-id="ede59-131">Você pode usar essa classe durante a implementação do seu objeto de valor real, assim como acontece com o objeto de valor Endereço mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="ede59-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

    public Address() { }

    public Address(string street, string city, string state, string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetEqualityComponents()
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

<span data-ttu-id="ede59-132">Você pode ver como essa implementação de objeto de valor do Endereço não tem nenhuma identidade e, portanto, nenhum campo de ID, nem na classe Address, nem mesmo na classe ValueObject.</span><span class="sxs-lookup"><span data-stu-id="ede59-132">You can see how this value object implementation of Address has no identity and therefore, no ID field, neither at the Address class not even at the ValueObject class.</span></span>

<span data-ttu-id="ede59-133">Não foi possível ter nenhum campo de ID em uma classe a ser usado pelo Entity Framework (EF) até EF Core 2,0, o que ajuda muito a implementar objetos de valor melhores sem ID.</span><span class="sxs-lookup"><span data-stu-id="ede59-133">Having no ID field in a class to be used by Entity Framework (EF) was not possible until EF Core 2.0, which greatly helps to implement better value objects with no ID.</span></span> <span data-ttu-id="ede59-134">Essa é justamente a explicação da próxima seção.</span><span class="sxs-lookup"><span data-stu-id="ede59-134">That is precisely the explanation of the next section.</span></span>

<span data-ttu-id="ede59-135">Pode ser argumentado que os objetos de valor, sendo imutáveis, devem ser somente leitura (ou seja, têm propriedades somente obtenção) e isso é verdade.</span><span class="sxs-lookup"><span data-stu-id="ede59-135">It could be argued that value objects, being immutable, should be read-only (that is, have get-only properties), and that's indeed true.</span></span> <span data-ttu-id="ede59-136">No entanto, os objetos de valor geralmente são serializados e desserializados para passar pelas filas de mensagens e ser somente leitura interrompe o desserializador de atribuir valores, de modo que você apenas os deixa como `private set` , o que é somente leitura o suficiente para ser prático.</span><span class="sxs-lookup"><span data-stu-id="ede59-136">However, value objects are usually serialized and deserialized to go through message queues, and being read-only stops the deserializer from assigning values, so you just leave them as `private set`, which is read-only enough to be practical.</span></span>

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20-and-later"></a><span data-ttu-id="ede59-137">Como persistir objetos de valor no banco de dados com EF Core 2,0 e posterior</span><span class="sxs-lookup"><span data-stu-id="ede59-137">How to persist value objects in the database with EF Core 2.0 and later</span></span>

<span data-ttu-id="ede59-138">Você acabou de ver como definir um objeto de valor em seu modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="ede59-138">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="ede59-139">Mas como você pode realmente mantê-lo no banco de dados usando Entity Framework Core, já que ele normalmente visa entidades com identidade?</span><span class="sxs-lookup"><span data-stu-id="ede59-139">But how can you actually persist it into the database using Entity Framework Core since it usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="ede59-140">Tela de fundo e abordagens mais antigas usando EF Core 1.1</span><span class="sxs-lookup"><span data-stu-id="ede59-140">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="ede59-141">Como segundo plano, uma limitação ao usar EF Core 1,0 e 1,1 era que você não podia usar [tipos complexos](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) , conforme definido no EF 6. x na .NET Framework tradicional.</span><span class="sxs-lookup"><span data-stu-id="ede59-141">As background, a limitation when using EF Core 1.0 and 1.1 was that you could not use [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="ede59-142">Portanto, se estiver usando EF Core 1.0 ou 1.1, precisará armazenar seu objeto de valor como uma entidade EF com um campo de ID.</span><span class="sxs-lookup"><span data-stu-id="ede59-142">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="ede59-143">Então, para que se pareça mais com um objeto de valor sem nenhuma identidade, você pode ocultar a ID para deixar claro que a identidade de um objeto de valor não é importante no modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="ede59-143">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="ede59-144">Você pode ocultar essa ID usando a ID como um [propriedade de sombra](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span><span class="sxs-lookup"><span data-stu-id="ede59-144">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="ede59-145">Uma vez que a configuração para ocultar a ID do modelo é configurada no nível de infraestrutura do EF, seria transparente para o seu modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="ede59-145">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="ede59-146">Na versão inicial do eShopOnContainers (.NET Core 1.1), a ID oculta necessária para a infraestrutura do EF Core foi implementada da seguinte maneira no nível de DbContext, usando a API Fluente no projeto de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="ede59-146">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="ede59-147">Portanto, a ID foi oculta do ponto de vista do domínio modelo de domínio, mas ainda está na infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="ede59-147">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

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

<span data-ttu-id="ede59-148">No entanto, a persistência desse objeto de valor no banco de dados foi executada como uma entidade normal em uma tabela diferente.</span><span class="sxs-lookup"><span data-stu-id="ede59-148">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="ede59-149">Com o EF Core 2,0 e posterior, há novas e melhores maneiras de persistir objetos de valor.</span><span class="sxs-lookup"><span data-stu-id="ede59-149">With EF Core 2.0 and later, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20-and-later"></a><span data-ttu-id="ede59-150">Persistir objetos de valor como tipos de entidade pertencentes no EF Core 2,0 e posterior</span><span class="sxs-lookup"><span data-stu-id="ede59-150">Persist value objects as owned entity types in EF Core 2.0 and later</span></span>

<span data-ttu-id="ede59-151">Mesmo com algumas lacunas entre o padrão de objeto de valor canônico em DDD e o tipo de entidade de propriedade no EF Core, atualmente, é a melhor maneira de persistir objetos de valor com o EF Core 2,0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="ede59-151">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0 and later.</span></span> <span data-ttu-id="ede59-152">Você pode ver as limitações no final desta seção.</span><span class="sxs-lookup"><span data-stu-id="ede59-152">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="ede59-153">O recurso de tipo de entidade própria foi adicionado ao EF Core desde a versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="ede59-153">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="ede59-154">Um tipo de entidade própria permite mapear tipos que não têm a própria identidade definida explicitamente no modelo de domínio e são usados como propriedades, como um objeto de valor, em uma de suas entidades.</span><span class="sxs-lookup"><span data-stu-id="ede59-154">An owned entity type allows you to map types that do not have their own identity explicitly defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="ede59-155">Um tipo de entidade de propriedade compartilha o mesmo tipo CLR com outro tipo de entidade (ou seja, é apenas uma classe regular).</span><span class="sxs-lookup"><span data-stu-id="ede59-155">An owned entity type shares the same CLR type with another entity type (that is, it's just a regular class).</span></span> <span data-ttu-id="ede59-156">A entidade que contém a navegação de definição é a entidade proprietária.</span><span class="sxs-lookup"><span data-stu-id="ede59-156">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="ede59-157">Ao consultar o proprietário, os tipos próprios serão incluídos por padrão.</span><span class="sxs-lookup"><span data-stu-id="ede59-157">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="ede59-158">Apenas olhando o modelo de domínio, um tipo de propriedade parece que ele não tem nenhuma identidade.</span><span class="sxs-lookup"><span data-stu-id="ede59-158">Just by looking at the domain model, an owned type looks like it doesn't have any identity.</span></span> <span data-ttu-id="ede59-159">No entanto, nos bastidores, os tipos de propriedade têm a identidade, mas a propriedade de navegação do proprietário faz parte dessa identidade.</span><span class="sxs-lookup"><span data-stu-id="ede59-159">However, under the covers, owned types do have the identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="ede59-160">A identidade de instâncias de tipos próprios não é completamente própria.</span><span class="sxs-lookup"><span data-stu-id="ede59-160">The identity of instances of owned types is not completely their own.</span></span> <span data-ttu-id="ede59-161">Consiste em três componentes:</span><span class="sxs-lookup"><span data-stu-id="ede59-161">It consists of three components:</span></span>

- <span data-ttu-id="ede59-162">A identidade do proprietário</span><span class="sxs-lookup"><span data-stu-id="ede59-162">The identity of the owner</span></span>

- <span data-ttu-id="ede59-163">A propriedade de navegação apontando para elas</span><span class="sxs-lookup"><span data-stu-id="ede59-163">The navigation property pointing to them</span></span>

- <span data-ttu-id="ede59-164">No caso de coleções de tipos de propriedade, um componente independente (com suporte no EF Core 2,2 e posterior).</span><span class="sxs-lookup"><span data-stu-id="ede59-164">In the case of collections of owned types, an independent component (supported in EF Core 2.2 and later).</span></span>

<span data-ttu-id="ede59-165">Por exemplo, no modelo de domínio Ordenação em eShopOnContainers, como parte da entidade de Ordem, o objeto de valor de endereço é implementado como um tipo de entidade própria dentro da entidade de proprietário, que é a entidade Ordem.</span><span class="sxs-lookup"><span data-stu-id="ede59-165">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="ede59-166">`Address` é um tipo sem nenhuma propriedade de identidade definida no modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="ede59-166">`Address` is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="ede59-167">Ele é usado como uma propriedade do tipo Ordem para especificar o endereço para entrega para uma ordem específica.</span><span class="sxs-lookup"><span data-stu-id="ede59-167">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="ede59-168">Por convenção, uma chave primária de sombra será criada para o tipo próprio e será mapeada para a mesma tabela que a do proprietário usando a divisão de tabela.</span><span class="sxs-lookup"><span data-stu-id="ede59-168">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="ede59-169">Isso permite usar tipos próprios de modo similar a como os tipos complexos são usados no EF6 no .NET Framework tradicional.</span><span class="sxs-lookup"><span data-stu-id="ede59-169">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="ede59-170">É importante observar que tipos próprios nunca são descobertos pela convenção no núcleo do EF, assim, você precisa declará-los explicitamente.</span><span class="sxs-lookup"><span data-stu-id="ede59-170">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="ede59-171">No eShopOnContainers, no arquivo OrderingContext.cs, dentro do `OnModelCreating()` método, várias configurações de infraestrutura são aplicadas.</span><span class="sxs-lookup"><span data-stu-id="ede59-171">In eShopOnContainers, in the OrderingContext.cs file, within the `OnModelCreating()` method, multiple infrastructure configurations are applied.</span></span> <span data-ttu-id="ede59-172">Um deles está relacionado à entidade Ordem.</span><span class="sxs-lookup"><span data-stu-id="ede59-172">One of them is related to the Order entity.</span></span>

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

<span data-ttu-id="ede59-173">No código a seguir, a infraestrutura de persistência é definida para a entidade Ordem:</span><span class="sxs-lookup"><span data-stu-id="ede59-173">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

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

<span data-ttu-id="ede59-174">No código anterior, o método `orderConfiguration.OwnsOne(o => o.Address)` especifica que a propriedade `Address` é uma entidade própria do tipo `Order`.</span><span class="sxs-lookup"><span data-stu-id="ede59-174">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="ede59-175">Por padrão, as colunas de nome e banco de dados de convenções do EF Core para as propriedades do tipo de entidade própria como `EntityProperty_OwnedEntityProperty`.</span><span class="sxs-lookup"><span data-stu-id="ede59-175">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="ede59-176">Portanto, as propriedades internas do aparecerão `Address` na `Orders` tabela com os nomes `Address_Street` `Address_City` (e assim por diante para `State` , `Country` e `ZipCode` ).</span><span class="sxs-lookup"><span data-stu-id="ede59-176">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country`, and `ZipCode`).</span></span>

<span data-ttu-id="ede59-177">Você pode acrescentar o método fluente `Property().HasColumnName()` para renomear as colunas.</span><span class="sxs-lookup"><span data-stu-id="ede59-177">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="ede59-178">No caso em que `Address` é uma propriedade pública, os mapeamentos seriam semelhantes ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="ede59-178">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="ede59-179">É possível encadear o `OwnsOne` método em um mapeamento fluente.</span><span class="sxs-lookup"><span data-stu-id="ede59-179">It's possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="ede59-180">No exemplo hipotético a seguir, `OrderDetails` tem `BillingAddress` e `ShippingAddress`, que são tipos `Address`.</span><span class="sxs-lookup"><span data-stu-id="ede59-180">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="ede59-181">Então `OrderDetails` pertence ao tipo `Order`.</span><span class="sxs-lookup"><span data-stu-id="ede59-181">Then `OrderDetails` is owned by the `Order` type.</span></span>

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

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="ede59-182">Detalhes adicionais sobre tipos de entidade própria</span><span class="sxs-lookup"><span data-stu-id="ede59-182">Additional details on owned entity types</span></span>

- <span data-ttu-id="ede59-183">Os tipos próprios são definidos quando você configura uma propriedade de navegação com um tipo específico usando a API fluente OwnsOne.</span><span class="sxs-lookup"><span data-stu-id="ede59-183">Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

- <span data-ttu-id="ede59-184">A definição de um tipo próprio em nosso modelo de metadados é uma composição de: o tipo de proprietário, a propriedade de navegação e o tipo CLR do tipo próprio.</span><span class="sxs-lookup"><span data-stu-id="ede59-184">The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

- <span data-ttu-id="ede59-185">A identidade (chave) de uma instância de tipo próprio na nossa pilha é uma composição da identidade do tipo de proprietário e a definição do tipo próprio.</span><span class="sxs-lookup"><span data-stu-id="ede59-185">The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="ede59-186">Recursos de entidades de propriedade</span><span class="sxs-lookup"><span data-stu-id="ede59-186">Owned entities capabilities</span></span>

- <span data-ttu-id="ede59-187">Os tipos próprios podem referenciar outras entidades, tanto próprias (tipos próprios aninhados) quanto não próprias (propriedades de navegação de referência comuns para outras entidades).</span><span class="sxs-lookup"><span data-stu-id="ede59-187">Owned types can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

- <span data-ttu-id="ede59-188">Você pode mapear o mesmo tipo CLR como diferentes tipos próprios na mesma entidade de proprietário por meio de propriedades de navegação separadas.</span><span class="sxs-lookup"><span data-stu-id="ede59-188">You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

- <span data-ttu-id="ede59-189">A divisão de tabela é configurada por convenção, mas você pode recusar mapeando o tipo de propriedade para uma tabela diferente usando ToTable.</span><span class="sxs-lookup"><span data-stu-id="ede59-189">Table splitting is set up by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

- <span data-ttu-id="ede59-190">O carregamento adiantado é executado automaticamente em tipos de propriedade, ou seja, não há necessidade de chamar `.Include()` na consulta.</span><span class="sxs-lookup"><span data-stu-id="ede59-190">Eager loading is performed automatically on owned types, that is, there's no need to call `.Include()` on the query.</span></span>

- <span data-ttu-id="ede59-191">Pode ser configurado com o atributo `[Owned]` , usando EF Core 2,1 e posterior.</span><span class="sxs-lookup"><span data-stu-id="ede59-191">Can be configured with attribute `[Owned]`, using EF Core 2.1 and later.</span></span>

- <span data-ttu-id="ede59-192">Pode lidar com coleções de tipos de propriedade (usando a versão 2,2 e posteriores).</span><span class="sxs-lookup"><span data-stu-id="ede59-192">Can handle collections of owned types (using version 2.2 and later).</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="ede59-193">Limitações de entidades pertencentes</span><span class="sxs-lookup"><span data-stu-id="ede59-193">Owned entities limitations</span></span>

- <span data-ttu-id="ede59-194">Você não pode criar um `DbSet<T>` de um tipo de propriedade (por Design).</span><span class="sxs-lookup"><span data-stu-id="ede59-194">You can't create a `DbSet<T>` of an owned type (by design).</span></span>

- <span data-ttu-id="ede59-195">Você não pode chamar `ModelBuilder.Entity<T>()` em tipos de propriedade (atualmente por Design).</span><span class="sxs-lookup"><span data-stu-id="ede59-195">You can't call `ModelBuilder.Entity<T>()` on owned types (currently by design).</span></span>

- <span data-ttu-id="ede59-196">Não há suporte para tipos de propriedade opcionais (ou seja, anuláveis) que são mapeados com o proprietário na mesma tabela (ou seja, usando divisão de tabela).</span><span class="sxs-lookup"><span data-stu-id="ede59-196">No support for optional (that is, nullable) owned types that are mapped with the owner in the same table (that is, using table splitting).</span></span> <span data-ttu-id="ede59-197">Isso ocorre porque o mapeamento é feito para cada propriedade, não há um sentinela separado para o valor complexo nulo como um todo.</span><span class="sxs-lookup"><span data-stu-id="ede59-197">This is because mapping is done for each property, there is no  separate sentinel for the null complex value as a whole.</span></span>

- <span data-ttu-id="ede59-198">Não há suporte para mapeamento de herança para tipos de propriedade, mas você deve ser capaz de mapear dois tipos folha das mesmas hierarquias de herança como tipos de propriedade diferentes.</span><span class="sxs-lookup"><span data-stu-id="ede59-198">No inheritance-mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="ede59-199">O EF Core não argumentará sobre o fato de que fazem parte da mesma hierarquia.</span><span class="sxs-lookup"><span data-stu-id="ede59-199">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="ede59-200">Principais diferenças com tipos complexos do EF6</span><span class="sxs-lookup"><span data-stu-id="ede59-200">Main differences with EF6's complex types</span></span>

- <span data-ttu-id="ede59-201">A divisão de tabela é opcional, ou seja, pode, opcionalmente, ser mapeada para uma tabela separada e ainda ser de tipos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="ede59-201">Table splitting is optional, that is, they can optionally be mapped to a separate table and still be owned types.</span></span>

- <span data-ttu-id="ede59-202">Eles podem referenciar outras entidades (ou seja, eles podem atuar como o lado dependente em relações com outros tipos de propriedade diferente).</span><span class="sxs-lookup"><span data-stu-id="ede59-202">They can reference other entities (that is, they can act as the dependent side on relationships to other non-owned types).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ede59-203">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="ede59-203">Additional resources</span></span>

- <span data-ttu-id="ede59-204">**Martin Fowler. Padrão valorobject** </span><span class="sxs-lookup"><span data-stu-id="ede59-204">**Martin Fowler. ValueObject pattern** </span></span>\
  <https://martinfowler.com/bliki/ValueObject.html>

- <span data-ttu-id="ede59-205">**Eric Evans. Design controlado por domínio: solução de complexidade no coração do software.**</span><span class="sxs-lookup"><span data-stu-id="ede59-205">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="ede59-206">(Livro; inclui uma discussão sobre objetos de valor) </span><span class="sxs-lookup"><span data-stu-id="ede59-206">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="ede59-207">**Vaughn Vernon. Implementando o design controlado por domínio.**</span><span class="sxs-lookup"><span data-stu-id="ede59-207">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="ede59-208">(Livro; inclui uma discussão sobre objetos de valor) </span><span class="sxs-lookup"><span data-stu-id="ede59-208">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="ede59-209">**Tipos de entidade pertencentes** </span><span class="sxs-lookup"><span data-stu-id="ede59-209">**Owned Entity Types** </span></span>\
  <https://docs.microsoft.com/ef/core/modeling/owned-entities>

- <span data-ttu-id="ede59-210">**Propriedades da sombra** </span><span class="sxs-lookup"><span data-stu-id="ede59-210">**Shadow Properties** </span></span>\
  <https://docs.microsoft.com/ef/core/modeling/shadow-properties>

- <span data-ttu-id="ede59-211">**Tipos complexos e/ou objetos de valor**.</span><span class="sxs-lookup"><span data-stu-id="ede59-211">**Complex types and/or value objects**.</span></span> <span data-ttu-id="ede59-212">Discussão no repositório GitHub do EF Core (guia Problemas) </span><span class="sxs-lookup"><span data-stu-id="ede59-212">Discussion in the EF Core GitHub repo (Issues tab) </span></span>\
  <https://github.com/dotnet/efcore/issues/246>

- <span data-ttu-id="ede59-213">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="ede59-213">**ValueObject.cs.**</span></span> <span data-ttu-id="ede59-214">Classe de objeto de valor base no eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="ede59-214">Base value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- <span data-ttu-id="ede59-215">**Classe de endereços.**</span><span class="sxs-lookup"><span data-stu-id="ede59-215">**Address class.**</span></span> <span data-ttu-id="ede59-216">Exemplo de classe de objeto de valor em eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="ede59-216">Sample value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> <span data-ttu-id="ede59-217">[Anterior](seedwork-domain-model-base-classes-interfaces.md) 
>  [Avançar](enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="ede59-217">[Previous](seedwork-domain-model-base-classes-interfaces.md)
[Next](enumeration-classes-over-enum-types.md)</span></span>
