---
title: Propriedades
description: Saiba mais sobre propriedades C#, que incluem recursos de validação, valores computados, avaliação lenta e notificações de alteração de propriedade.
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 04/03/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 6950d25a-bba1-4744-b7c7-a3cc90438c55
ms.openlocfilehash: 2a25919048f94211b1696ac8c8471a14ce6e15c5
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="properties"></a><span data-ttu-id="a4134-104">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a4134-104">Properties</span></span>

<span data-ttu-id="a4134-105">As propriedades são cidadãos de primeira classe no C#.</span><span class="sxs-lookup"><span data-stu-id="a4134-105">Properties are first class citizens in C#.</span></span> <span data-ttu-id="a4134-106">A linguagem define uma sintaxe que permite aos desenvolvedores escrever código que expresse sua intenção de design com precisão.</span><span class="sxs-lookup"><span data-stu-id="a4134-106">The language defines syntax that enables developers to write code that accurately expresses their design intent.</span></span>

<span data-ttu-id="a4134-107">As propriedades se comportam como campos quando são acessadas.</span><span class="sxs-lookup"><span data-stu-id="a4134-107">Properties behave like fields when they are accessed.</span></span>
<span data-ttu-id="a4134-108">No entanto, diferentemente dos campos, as propriedades são implementadas com acessadores, que definem as instruções que são executadas quando uma propriedade é acessada ou atribuída.</span><span class="sxs-lookup"><span data-stu-id="a4134-108">However, unlike fields, properties are implemented with accessors that define the statements executed when a property is accessed or assigned.</span></span>

## <a name="property-syntax"></a><span data-ttu-id="a4134-109">Sintaxe de propriedade</span><span class="sxs-lookup"><span data-stu-id="a4134-109">Property Syntax</span></span>

<span data-ttu-id="a4134-110">A sintaxe para propriedades é uma extensão natural para os campos.</span><span class="sxs-lookup"><span data-stu-id="a4134-110">The syntax for properties is a natural extension to fields.</span></span> <span data-ttu-id="a4134-111">Um campo define um local de armazenamento:</span><span class="sxs-lookup"><span data-stu-id="a4134-111">A field defines a storage location:</span></span>

```csharp
public class Person
{
    public string FirstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="a4134-112">Uma definição de propriedade contém declarações para um acessador `get` e `set` que recupera e atribui o valor dessa propriedade:</span><span class="sxs-lookup"><span data-stu-id="a4134-112">A property definition contains declarations for a `get` and `set` accessor that retrieves and assigns the value of that property:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="a4134-113">A sintaxe mostrada acima é a sintaxe da *propriedade automática*.</span><span class="sxs-lookup"><span data-stu-id="a4134-113">The syntax shown above is the *auto property* syntax.</span></span> <span data-ttu-id="a4134-114">O compilador gera o local de armazenamento para o campo que dá suporte à propriedade.</span><span class="sxs-lookup"><span data-stu-id="a4134-114">The compiler generates the storage location for the field that backs up the property.</span></span> <span data-ttu-id="a4134-115">O compilador também implementa o corpo dos acessadores `get` e `set`.</span><span class="sxs-lookup"><span data-stu-id="a4134-115">The compiler also implements the body of the `get` and `set` accessors.</span></span>

<span data-ttu-id="a4134-116">Às vezes, você precisa inicializar uma propriedade para um valor diferente do padrão para seu tipo.</span><span class="sxs-lookup"><span data-stu-id="a4134-116">Sometimes, you need to initialize a property to a value other than the default for its type.</span></span>  <span data-ttu-id="a4134-117">O C# permite isso definindo um valor após a chave de fechamento da propriedade.</span><span class="sxs-lookup"><span data-stu-id="a4134-117">C# enables that by setting a value after the closing brace for the property.</span></span> <span data-ttu-id="a4134-118">Você pode preferir que o valor inicial para a propriedade `FirstName` seja a cadeia de caracteres vazia em vez de `null`.</span><span class="sxs-lookup"><span data-stu-id="a4134-118">You may prefer the initial value for the `FirstName` property to be the empty string rather than `null`.</span></span> <span data-ttu-id="a4134-119">Você deve especificar isso conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="a4134-119">You would specify that as shown below:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; } = string.Empty;

    // remaining implementation removed from listing
}
```

<span data-ttu-id="a4134-120">Isso é mais útil para propriedades somente leitura, como você verá posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="a4134-120">This is most useful for read-only properties, as you'll see later in this topic.</span></span>

<span data-ttu-id="a4134-121">Você mesmo também pode definir o armazenamento, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="a4134-121">You can also define the storage yourself, as shown below:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get { return firstName; }
        set { firstName = value; }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="a4134-122">Quando uma implementação de propriedade é uma única expressão, você pode usar *membros aptos para expressão* para o getter ou setter:</span><span class="sxs-lookup"><span data-stu-id="a4134-122">When a property implementation is a single expression, you can use *expression-bodied members* for the getter or setter:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set => firstName = value;
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="a4134-123">Essa sintaxe simplificada será usada quando aplicável ao longo deste tópico.</span><span class="sxs-lookup"><span data-stu-id="a4134-123">This simplified syntax will be used where applicable throughout this topic.</span></span>

<span data-ttu-id="a4134-124">A definição da propriedade mostrada acima é uma propriedade de leitura/gravação.</span><span class="sxs-lookup"><span data-stu-id="a4134-124">The property definition shown above is a read-write property.</span></span> <span data-ttu-id="a4134-125">Observe a palavra-chave `value` no acessador set.</span><span class="sxs-lookup"><span data-stu-id="a4134-125">Notice the keyword `value` in the set accessor.</span></span> <span data-ttu-id="a4134-126">O acessador `set` sempre tem um parâmetro único chamado `value`.</span><span class="sxs-lookup"><span data-stu-id="a4134-126">The `set` accessor always has a single parameter named `value`.</span></span> <span data-ttu-id="a4134-127">O acessador `get` deve retornar um valor que seja conversível para o tipo da propriedade (`string`, neste exemplo).</span><span class="sxs-lookup"><span data-stu-id="a4134-127">The `get` accessor must return a value that is convertible to the type of the property (`string` in this example).</span></span>
 
<span data-ttu-id="a4134-128">Essas são as noções básicas sobre a sintaxe.</span><span class="sxs-lookup"><span data-stu-id="a4134-128">That's the basics of the syntax.</span></span> <span data-ttu-id="a4134-129">Há muitas variações diferentes que oferecem suporte a uma variedade de linguagens de design diferentes.</span><span class="sxs-lookup"><span data-stu-id="a4134-129">There are many different variations that support a variety of different design idioms.</span></span> <span data-ttu-id="a4134-130">Vamos explorá-las e conhecer as opções de sintaxe para cada uma.</span><span class="sxs-lookup"><span data-stu-id="a4134-130">Let's explore those, and learn the syntax options for each.</span></span>

## <a name="scenarios"></a><span data-ttu-id="a4134-131">Cenários</span><span class="sxs-lookup"><span data-stu-id="a4134-131">Scenarios</span></span>

<span data-ttu-id="a4134-132">Os exemplos acima mostraram um dos casos mais simples de definição de propriedade: uma propriedade de leitura/gravação sem validação.</span><span class="sxs-lookup"><span data-stu-id="a4134-132">The examples above showed one of the simplest cases of property definition: a read-write property with no validation.</span></span> <span data-ttu-id="a4134-133">Ao escrever o código que você deseja nos acessadores `get` e `set`, você pode criar vários cenários diferentes.</span><span class="sxs-lookup"><span data-stu-id="a4134-133">By writing the code you want in the `get` and `set` accessors, you can create many different scenarios.</span></span>

### <a name="validation"></a><span data-ttu-id="a4134-134">Validação</span><span class="sxs-lookup"><span data-stu-id="a4134-134">Validation</span></span>

<span data-ttu-id="a4134-135">Você pode escrever código no acessador `set` para garantir que os valores representados por uma propriedade sejam sempre válidos.</span><span class="sxs-lookup"><span data-stu-id="a4134-135">You can write code in the `set` accessor to ensure that the values represented by a property are always valid.</span></span> <span data-ttu-id="a4134-136">Por exemplo, suponha que uma regra para a classe `Person` é que o nome não pode ser um espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="a4134-136">For example, suppose one rule for the `Person` class is that the name cannot be blank, or whitespace.</span></span> <span data-ttu-id="a4134-137">Você escreveria isso da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a4134-137">You would write that as follows:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            firstName = value;
        }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="a4134-138">O exemplo acima aplica a regra de que o nome não deve ser em branco ou espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="a4134-138">The example above enforces the rule that the first name must not be blank, or whitespace.</span></span> <span data-ttu-id="a4134-139">Se um desenvolvedor escreve</span><span class="sxs-lookup"><span data-stu-id="a4134-139">If a developer writes</span></span>

```csharp
hero.FirstName = "";
```

<span data-ttu-id="a4134-140">Essa atribuição lança uma `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="a4134-140">That assignment throws an `ArgumentException`.</span></span> <span data-ttu-id="a4134-141">Como um acessador set de propriedade deve ter um tipo de retorno void, você relata erros no acessador set lançando uma exceção.</span><span class="sxs-lookup"><span data-stu-id="a4134-141">Because a property set accessor must have a void return type, you report errors in the set accessor by throwing an exception.</span></span>

<span data-ttu-id="a4134-142">Esse é um caso simples de validação.</span><span class="sxs-lookup"><span data-stu-id="a4134-142">That is a simple case of validation.</span></span> <span data-ttu-id="a4134-143">Você pode estender essa mesma sintaxe para qualquer coisa necessária em seu cenário.</span><span class="sxs-lookup"><span data-stu-id="a4134-143">You can extend this same syntax to anything needed in your scenario.</span></span> <span data-ttu-id="a4134-144">Você pode verificar as relações entre diferentes propriedades ou validar em relação a qualquer condição externa.</span><span class="sxs-lookup"><span data-stu-id="a4134-144">You can check the relationships between different properties, or validate against any external conditions.</span></span> <span data-ttu-id="a4134-145">Todas as instruções de C# válidas são válidas em um acessador de propriedade.</span><span class="sxs-lookup"><span data-stu-id="a4134-145">Any valid C# statements are valid in a property accessor.</span></span>

### <a name="read-only"></a><span data-ttu-id="a4134-146">Somente leitura</span><span class="sxs-lookup"><span data-stu-id="a4134-146">Read-only</span></span>

<span data-ttu-id="a4134-147">Até aqui, todas as definições de propriedade que você viu são de propriedades de leitura/gravação com acessadores públicos.</span><span class="sxs-lookup"><span data-stu-id="a4134-147">Up to this point, all the property definitions you have seen are read/write properties with public accessors.</span></span> <span data-ttu-id="a4134-148">Essa não é a única acessibilidade válida para as propriedades.</span><span class="sxs-lookup"><span data-stu-id="a4134-148">That's not the only valid accessibility for properties.</span></span>
<span data-ttu-id="a4134-149">Você pode criar propriedades somente leitura ou dar acessibilidade diferente aos acessadores get e set.</span><span class="sxs-lookup"><span data-stu-id="a4134-149">You can create read-only properties, or give different accessibility to the set and get accessors.</span></span> <span data-ttu-id="a4134-150">Suponha que sua classe `Person` só deva habilitar a alteração do valor da propriedade `FirstName` em outros métodos naquela classe.</span><span class="sxs-lookup"><span data-stu-id="a4134-150">Suppose that your `Person` class should only enable changing the value of the `FirstName` property from other methods in that class.</span></span> <span data-ttu-id="a4134-151">Você pode dar acessibilidade `private` ao acessador set, em vez de `public`:</span><span class="sxs-lookup"><span data-stu-id="a4134-151">You could give the set accessor `private` accessibility instead of `public`:</span></span>

```csharp
public class Person
{
    public string FirstName { get; private set; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="a4134-152">Agora, a propriedade `FirstName` pode ser acessada de qualquer código, mas só pode ser atribuída de outro código na classe `Person`.</span><span class="sxs-lookup"><span data-stu-id="a4134-152">Now, the `FirstName` property can be accessed from any code, but it can only be assigned from other code in the `Person` class.</span></span>

<span data-ttu-id="a4134-153">Você pode adicionar qualquer modificador de acesso restritivo aos acessadores get ou set.</span><span class="sxs-lookup"><span data-stu-id="a4134-153">You can add any restrictive access modifier to either the set or get accessors.</span></span> <span data-ttu-id="a4134-154">Nenhum modificador de acesso que você colocar no acessador individual deve ser mais limitado que o modificador de acesso da definição de propriedade.</span><span class="sxs-lookup"><span data-stu-id="a4134-154">Any access modifier you place on the individual accessor must be more limited than the access modifier on the property definition.</span></span> <span data-ttu-id="a4134-155">O que está acima é válido porque a propriedade `FirstName` é `public`, mas o acessador set é `private`.</span><span class="sxs-lookup"><span data-stu-id="a4134-155">The above is legal because the `FirstName` property is `public`, but the set accessor is `private`.</span></span> <span data-ttu-id="a4134-156">Você não pode declarar uma propriedade `private` com um acessador `public`.</span><span class="sxs-lookup"><span data-stu-id="a4134-156">You could not declare a `private` property with a `public` accessor.</span></span> <span data-ttu-id="a4134-157">As declarações de propriedade também podem ser declaradas `protected`, `internal`, `protected internal`, `private protected` ou até mesmo `private`.</span><span class="sxs-lookup"><span data-stu-id="a4134-157">Property declarations can also be declared `protected`, `internal`, `protected internal`, `private protected` or even `private`.</span></span>   

<span data-ttu-id="a4134-158">Também é válido colocar o modificador mais restritivo no acessador `get`.</span><span class="sxs-lookup"><span data-stu-id="a4134-158">It is also legal to place the more restrictive modifier on the `get` accessor.</span></span> <span data-ttu-id="a4134-159">Por exemplo, você poderia ter uma propriedade `public`, mas restringir o acessador `get` como `private`.</span><span class="sxs-lookup"><span data-stu-id="a4134-159">For example, you could have a `public` property, but restrict the `get` accessor to `private`.</span></span> <span data-ttu-id="a4134-160">Esse cenário raramente acontece na prática.</span><span class="sxs-lookup"><span data-stu-id="a4134-160">That scenario is rarely done in practice.</span></span>

<span data-ttu-id="a4134-161">Você também pode restringir modificações a uma propriedade para que ela possa ser definida somente em um construtor ou um inicializador de propriedade.</span><span class="sxs-lookup"><span data-stu-id="a4134-161">You can also restrict modifications to a property so that it can only be set in a constructor or a property initializer.</span></span> <span data-ttu-id="a4134-162">Você pode modificar a classe `Person` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a4134-162">You can modify the `Person` class so as follows:</span></span>

```csharp
public class Person
{
    public Person(string firstName)
    {
        this.FirstName = firstName;
    }

    public string FirstName { get; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="a4134-163">Esse recurso é mais comumente usado para inicializar coleções que são expostas como propriedades somente leitura:</span><span class="sxs-lookup"><span data-stu-id="a4134-163">This feature is most commonly used for initializing collections that are exposed as read-only properties:</span></span>

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a><span data-ttu-id="a4134-164">Propriedades computadas</span><span class="sxs-lookup"><span data-stu-id="a4134-164">Computed Properties</span></span>

<span data-ttu-id="a4134-165">Uma propriedade não precisa simplesmente retornar o valor de um campo de membro.</span><span class="sxs-lookup"><span data-stu-id="a4134-165">A property does not need to simply return the value of a member field.</span></span> <span data-ttu-id="a4134-166">Você pode criar propriedades que retornam um valor computado.</span><span class="sxs-lookup"><span data-stu-id="a4134-166">You can create properties that return a computed value.</span></span> <span data-ttu-id="a4134-167">Vamos expandir o objeto `Person` para retornar o nome completo, computado pela concatenação dos nomes e sobrenomes:</span><span class="sxs-lookup"><span data-stu-id="a4134-167">Let's expand the `Person` object to return the full name, computed by concatenating the first and last names:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName { get { return $"{FirstName} {LastName}"; } }
}
```

<span data-ttu-id="a4134-168">O exemplo acima usa o recurso de [interpolação de cadeia de caracteres](../csharp/language-reference/tokens/interpolated.md) para criar a cadeia de caracteres formatada do nome completo.</span><span class="sxs-lookup"><span data-stu-id="a4134-168">The example above uses the [string interpolation](../csharp/language-reference/tokens/interpolated.md) feature to create the formatted string for the full name.</span></span>

<span data-ttu-id="a4134-169">Você também pode usar *membros aptos para expressão*, que fornecem uma maneira mais sucinta de criar a propriedade `FullName` computada:</span><span class="sxs-lookup"><span data-stu-id="a4134-169">You can also use *expression-bodied members*, which provides a more succinct way to create the computed `FullName` property:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName =>  $"{FirstName} {LastName}";
}
```
 
<span data-ttu-id="a4134-170">Os *membros aptos para expressão* usam a sintaxe *expressão lambda* para definir um método que contenha uma única expressão.</span><span class="sxs-lookup"><span data-stu-id="a4134-170">*Expression-bodied members* use the *lambda expression* syntax to define a method that contain a single expression.</span></span> <span data-ttu-id="a4134-171">Aqui, essa expressão retorna o nome completo do objeto person.</span><span class="sxs-lookup"><span data-stu-id="a4134-171">Here, that expression returns the full name for the person object.</span></span>

### <a name="lazy-evaluated-properties"></a><span data-ttu-id="a4134-172">Propriedades avaliadas lentas</span><span class="sxs-lookup"><span data-stu-id="a4134-172">Lazy Evaluated Properties</span></span>

<span data-ttu-id="a4134-173">Você pode combinar o conceito de uma propriedade computada com o armazenamento e criar uma *propriedade avaliada lenta*.</span><span class="sxs-lookup"><span data-stu-id="a4134-173">You can mix the concept of a computed property with storage and create a *lazy evaluated property*.</span></span>  <span data-ttu-id="a4134-174">Por exemplo, você poderia atualizar a propriedade `FullName` para que a formatação da cadeia de caracteres só acontecesse na primeira vez que ela foi acessada:</span><span class="sxs-lookup"><span data-stu-id="a4134-174">For example, you could update the `FullName` property so that the string formatting only happened the first time it was accessed:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

<span data-ttu-id="a4134-175">No entanto, o código acima contém um bug.</span><span class="sxs-lookup"><span data-stu-id="a4134-175">The above code contains a bug though.</span></span> <span data-ttu-id="a4134-176">Se o código atualizar o valor das propriedades `FirstName` ou `LastName`, o campo `fullName`, anteriormente avaliado, será inválido.</span><span class="sxs-lookup"><span data-stu-id="a4134-176">If code updates the value of either the `FirstName` or `LastName` property, the previously evaluated `fullName` field is invalid.</span></span> <span data-ttu-id="a4134-177">Você precisa atualizar os acessadores `set` das propriedades `FirstName` e `LastName` para que o campo `fullName` seja calculado novamente:</span><span class="sxs-lookup"><span data-stu-id="a4134-177">You need to update the `set` accessors of the `FirstName` and `LastName` property so that the `fullName` field is calculated again:</span></span>

```csharp
public class Person
{
    private string firstName;
    public string FirstName
    {
        get => firstName;
        set
        {
            firstName = value;
            fullName = null;
        }
    }

    private string lastName;
    public string LastName
    {
        get => lastName;
        set
        {
            lastName = value;
            fullName = null;
        }
    }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

<span data-ttu-id="a4134-178">Esta versão final avalia a propriedade `FullName` apenas quando necessário.</span><span class="sxs-lookup"><span data-stu-id="a4134-178">This final version evaluates the `FullName` property only when needed.</span></span>
<span data-ttu-id="a4134-179">Se a versão calculada anteriormente for válida, ela será usada.</span><span class="sxs-lookup"><span data-stu-id="a4134-179">If the previously calculated version is valid, it's used.</span></span> <span data-ttu-id="a4134-180">Se outra alteração de estado invalidar a versão calculada anteriormente, ela será recalculada.</span><span class="sxs-lookup"><span data-stu-id="a4134-180">If another state change invalidates the previously calculated version, it will be recalculated.</span></span> <span data-ttu-id="a4134-181">Os desenvolvedores que usam essa classe não precisam saber dos detalhes da implementação.</span><span class="sxs-lookup"><span data-stu-id="a4134-181">Developers that use this class do not need to know the details of the implementation.</span></span> <span data-ttu-id="a4134-182">Nenhuma dessas alterações internas afetam o uso do objeto Person.</span><span class="sxs-lookup"><span data-stu-id="a4134-182">None of these internal changes affect the use of the Person object.</span></span> <span data-ttu-id="a4134-183">Esse é o motivo principal para o uso de propriedades para expor os membros de dados de um objeto.</span><span class="sxs-lookup"><span data-stu-id="a4134-183">That's the key reason for using Properties to expose data members of an object.</span></span>
 
### <a name="inotifypropertychanged"></a><span data-ttu-id="a4134-184">INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="a4134-184">INotifyPropertyChanged</span></span>

<span data-ttu-id="a4134-185">A última situação em que você precisa escrever código em um acessador de propriedade é para oferecer suporte à interface `INotifyPropertyChanged`, usada para notificar os clientes de vinculação de dados que um valor foi alterado.</span><span class="sxs-lookup"><span data-stu-id="a4134-185">A final scenario where you need to write code in a property accessor is to support the `INotifyPropertyChanged` interface used to notify data binding clients that a value has changed.</span></span> <span data-ttu-id="a4134-186">Quando o valor de uma propriedade for alterado, o objeto aciona o evento `PropertyChanged` para indicar a alteração.</span><span class="sxs-lookup"><span data-stu-id="a4134-186">When the value of a property changes, the object raises the `PropertyChanged` event to indicate the change.</span></span> <span data-ttu-id="a4134-187">As bibliotecas de vinculação de dados, por sua vez, atualizam os elementos de exibição com base nessa alteração.</span><span class="sxs-lookup"><span data-stu-id="a4134-187">The data binding libraries, in turn, update display elements based on that change.</span></span> <span data-ttu-id="a4134-188">O código a seguir mostra como você implementaria `INotifyPropertyChanged` para a propriedade `FirstName` dessa classe person.</span><span class="sxs-lookup"><span data-stu-id="a4134-188">The code below shows how you would implement `INotifyPropertyChanged` for the `FirstName` property of this person class.</span></span>

```csharp
public class Person : INotifyPropertyChanged
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            if (value != firstName)
            {
                PropertyChanged?.Invoke(this, 
                    new PropertyChangedEventArgs(nameof(FirstName)));
            }
            firstName = value;
        }
    }
    private string firstName;

    public event PropertyChangedEventHandler PropertyChanged;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="a4134-189">O operador `?.` é chamado de *operador condicional nulo*.</span><span class="sxs-lookup"><span data-stu-id="a4134-189">The `?.` operator is called the *null conditional operator*.</span></span> <span data-ttu-id="a4134-190">Ele verifica uma referência nula antes de avaliar o lado direito do operador.</span><span class="sxs-lookup"><span data-stu-id="a4134-190">It checks for a null reference before evaluating the right side of the operator.</span></span> <span data-ttu-id="a4134-191">O resultado final é que, se não houver nenhum assinante para o evento `PropertyChanged`, o código para acionar o evento não é executado.</span><span class="sxs-lookup"><span data-stu-id="a4134-191">The end result is that if there are no subscribers to the `PropertyChanged` event, the code to raise the event doesn't execute.</span></span> <span data-ttu-id="a4134-192">Ela lançaria uma `NullReferenceException` sem essa verificação, nesse caso.</span><span class="sxs-lookup"><span data-stu-id="a4134-192">It would throw a `NullReferenceException` without this check in that case.</span></span> <span data-ttu-id="a4134-193">Consulte a página sobre [`events`](delegates-events.md) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="a4134-193">See the page on [`events`](delegates-events.md) for more details.</span></span> <span data-ttu-id="a4134-194">Este exemplo também usa o novo operador `nameof` para converter o símbolo de nome da propriedade em sua representação de texto.</span><span class="sxs-lookup"><span data-stu-id="a4134-194">This example also uses the new `nameof` operator to convert from the property name symbol to its text representation.</span></span>
<span data-ttu-id="a4134-195">O uso de `nameof` pode reduzir erros no local em que você digitou errado o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="a4134-195">Using `nameof` can reduce errors where you have mistyped the name of the property.</span></span>

<span data-ttu-id="a4134-196">Novamente, este é um exemplo de um caso em que você pode escrever código em seus acessadores para dar suporte aos cenários você precisa.</span><span class="sxs-lookup"><span data-stu-id="a4134-196">Again, this is an example of a case where you can write code in your accessors to support the scenarios you need.</span></span>

## <a name="summing-up"></a><span data-ttu-id="a4134-197">Resumindo</span><span class="sxs-lookup"><span data-stu-id="a4134-197">Summing up</span></span>

<span data-ttu-id="a4134-198">As propriedades são uma forma de campos inteligentes em uma classe ou objeto.</span><span class="sxs-lookup"><span data-stu-id="a4134-198">Properties are a form of smart fields in a class or object.</span></span> <span data-ttu-id="a4134-199">De fora do objeto, elas parecem como campos no objeto.</span><span class="sxs-lookup"><span data-stu-id="a4134-199">From outside the object, they appear like fields in the object.</span></span> <span data-ttu-id="a4134-200">No entanto, as propriedades podem ser implementadas usando a paleta completa de funcionalidades do C#.</span><span class="sxs-lookup"><span data-stu-id="a4134-200">However, properties can be implemented using the full palette of C# functionality.</span></span>
<span data-ttu-id="a4134-201">Você pode fornecer validação, acessibilidade diferente, avaliação lenta ou quaisquer requisitos necessários aos seus cenários.</span><span class="sxs-lookup"><span data-stu-id="a4134-201">You can provide validation, different accessibility, lazy evaluation, or any requirements your scenarios need.</span></span>
