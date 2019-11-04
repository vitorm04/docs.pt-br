---
title: Inicializadores de objeto e coleção – Guia de Programação em C#
ms.custom: seodec18
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: 837be04208d438f15b4cc7c7124a47ef6c038cb2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455445"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="65c78-102">Inicializadores de objeto e coleção (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="65c78-102">Object and Collection Initializers (C# Programming Guide)</span></span>

<span data-ttu-id="65c78-103">O C# permite criar uma instância de um objeto ou uma coleção e executar as atribuições de membro em uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="65c78-103">C# lets you instantiate an object or collection and perform member assignments in a single statement.</span></span>

## <a name="object-initializers"></a><span data-ttu-id="65c78-104">Inicializadores de objeto</span><span class="sxs-lookup"><span data-stu-id="65c78-104">Object initializers</span></span>

<span data-ttu-id="65c78-105">Os inicializadores de objeto permitem atribuir valores a quaisquer campos ou propriedades acessíveis de um objeto na hora de criação sem que seja necessário invocar um construtor seguido por linhas de instruções de atribuição.</span><span class="sxs-lookup"><span data-stu-id="65c78-105">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="65c78-106">A sintaxe do inicializador de objeto permite especificar argumentos para um construtor ou omitir os argumentos (e a sintaxe de parênteses).</span><span class="sxs-lookup"><span data-stu-id="65c78-106">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="65c78-107">O exemplo a seguir mostra como usar um inicializador de objeto com um tipo nomeado, `Cat`, e como invocar o construtor sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="65c78-107">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the parameterless constructor.</span></span> <span data-ttu-id="65c78-108">Observe o uso de propriedades autoimplementadas na classe `Cat`.</span><span class="sxs-lookup"><span data-stu-id="65c78-108">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="65c78-109">Para obter mais informações, consulte [Propriedades autoimplementadas](auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="65c78-109">For more information, see [Auto-Implemented Properties](auto-implemented-properties.md).</span></span>  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  
 
<span data-ttu-id="65c78-110">A sintaxe dos inicializadores de objetos permite que você crie uma instância, e depois atribui o objeto recém-criado, com suas propriedades atribuídas, à variável na atribuição.</span><span class="sxs-lookup"><span data-stu-id="65c78-110">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>

<span data-ttu-id="65c78-111">Começando com o C# 6, os inicializadores de objeto podem definir indexadores, além de atribuir campos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="65c78-111">Starting with C# 6, object initializers can set indexers, in addition to assigning fields and properties.</span></span> <span data-ttu-id="65c78-112">Considere esta classe `Matrix` básica:</span><span class="sxs-lookup"><span data-stu-id="65c78-112">Consider this basic `Matrix` class:</span></span>

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

<span data-ttu-id="65c78-113">Você poderia inicializar a matriz de identidade com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="65c78-113">You could initialize the identity matrix with the following code:</span></span>

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

<span data-ttu-id="65c78-114">Nenhum indexador acessível que contenha um setter acessível pode ser usado como uma das expressões no inicializador de objeto, independentemente do número ou dos tipos de argumentos.</span><span class="sxs-lookup"><span data-stu-id="65c78-114">Any accessible indexer that contains an accessible setter can be used as one of the expressions in an object initializer, regardless of the number or types of arguments.</span></span> <span data-ttu-id="65c78-115">Os argumentos de índice formam o lado esquerdo da atribuição e o valor é o lado direito da expressão.</span><span class="sxs-lookup"><span data-stu-id="65c78-115">The index arguments form the left side of the assignment, and the value is the right side of the expression.</span></span>  <span data-ttu-id="65c78-116">Por exemplo, estes serão todos válidos se `IndexersExample` tiver os indexadores apropriados:</span><span class="sxs-lookup"><span data-stu-id="65c78-116">For example, these are all valid if `IndexersExample` has the appropriate indexers:</span></span>

```csharp
var thing = new IndexersExample {
    name = "object one",
    [1] = '1',
    [2] = '4',
    [3] = '9',
    Size = Math.PI,
    ['C',4] = "Middle C"
}
```

<span data-ttu-id="65c78-117">Para que o código anterior seja compilado, o tipo `IndexersExample` precisará ter os seguintes membros:</span><span class="sxs-lookup"><span data-stu-id="65c78-117">For the preceding code to compile, the `IndexersExample` type must have the following members:</span></span>

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
```

## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="65c78-118">Inicializadores de objeto com tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="65c78-118">Object Initializers with anonymous types</span></span>

<span data-ttu-id="65c78-119">Embora inicializadores de objetos possam ser usados em qualquer contexto, eles são especialmente úteis em expressões de consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="65c78-119">Although object initializers can be used in any context, they are especially useful in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="65c78-120">Expressões de consulta fazem uso frequente de [tipos anônimos](./anonymous-types.md), que podem ser inicializados somente usando um inicializador de objeto, como mostrado na declaração a seguir.</span><span class="sxs-lookup"><span data-stu-id="65c78-120">Query expressions make frequent use of [anonymous types](./anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

<span data-ttu-id="65c78-121">Os tipos anônimos habilitam a cláusula `select` em uma expressão de consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] a transformar objetos da sequência original em objetos cujo valor e forma podem diferir dos originais.</span><span class="sxs-lookup"><span data-stu-id="65c78-121">Anonymous types enable the `select` clause in a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="65c78-122">Isso será útil se você desejar armazenar apenas uma parte das informações de cada objeto em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="65c78-122">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="65c78-123">No exemplo a seguir, suponha que um objeto de produto (`p`) contenha vários campos e métodos e que você esteja apenas interessado em criar uma sequência de objetos que contenha o nome do produto e o preço unitário.</span><span class="sxs-lookup"><span data-stu-id="65c78-123">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

<span data-ttu-id="65c78-124">Quando essa consulta for executada, a variável `productInfos` conterá uma sequência de objetos que podem ser acessados em uma instrução `foreach` como mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="65c78-124">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  

```csharp
foreach(var p in productInfos){...}  
```

<span data-ttu-id="65c78-125">Cada objeto no novo tipo anônimo tem duas propriedades públicas que recebem os mesmos nomes que as propriedades ou os campos no objeto original.</span><span class="sxs-lookup"><span data-stu-id="65c78-125">Each object in the new anonymous type has two public properties that receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="65c78-126">Você também poderá renomear um campo quando estiver criando um tipo anônimo; o exemplo a seguir renomeia o campo `UnitPrice` como `Price`.</span><span class="sxs-lookup"><span data-stu-id="65c78-126">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a><span data-ttu-id="65c78-127">Inicializadores de coleção</span><span class="sxs-lookup"><span data-stu-id="65c78-127">Collection initializers</span></span>

<span data-ttu-id="65c78-128">Os inicializadores de coleção permitem especificar um ou mais inicializadores de elemento quando você inicializa um tipo de coleção que implementa <xref:System.Collections.IEnumerable> e tem `Add` com a assinatura apropriada como um método de instância ou um método de extensão.</span><span class="sxs-lookup"><span data-stu-id="65c78-128">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="65c78-129">Os inicializadores de elemento podem ser um valor simples, uma expressão ou um inicializador de objeto.</span><span class="sxs-lookup"><span data-stu-id="65c78-129">The element initializers can be a simple value, an expression, or an object initializer.</span></span> <span data-ttu-id="65c78-130">Ao usar um inicializador de coleção, você não precisa especificar várias chamadas. O compilador adiciona as chamadas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="65c78-130">By using a collection initializer, you do not have to specify multiple calls; the compiler adds the calls automatically.</span></span>  
  
<span data-ttu-id="65c78-131">O exemplo a seguir mostra dois inicializadores de coleção simples:</span><span class="sxs-lookup"><span data-stu-id="65c78-131">The following example shows two simple collection initializers:</span></span>  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

<span data-ttu-id="65c78-132">O inicializador de coleção a seguir usa inicializadores de objeto para inicializar objetos da classe `Cat` definida em um exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="65c78-132">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="65c78-133">Observe que os inicializadores de objeto individuais são envolvidos por chaves e separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="65c78-133">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
<span data-ttu-id="65c78-134">Você poderá especificar [nulo](../../language-reference/keywords/null.md) como um elemento em um inicializador de coleção se o método `Add` da coleção permitir.</span><span class="sxs-lookup"><span data-stu-id="65c78-134">You can specify [null](../../language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 <span data-ttu-id="65c78-135">É possível especificar elementos indexados quando a coleção é compatível com indexação de leitura/gravação.</span><span class="sxs-lookup"><span data-stu-id="65c78-135">You can specify indexed elements if the collection supports read / write indexing.</span></span>
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

<span data-ttu-id="65c78-136">O exemplo anterior gera o código que chama o <xref:System.Collections.Generic.Dictionary%602.Item(%600)> para definir os valores.</span><span class="sxs-lookup"><span data-stu-id="65c78-136">The preceding sample generates code that calls the <xref:System.Collections.Generic.Dictionary%602.Item(%600)> to set the values.</span></span> <span data-ttu-id="65c78-137">Antes C# de 6, você poderia inicializar dicionários e outros contêineres associativos usando a sintaxe a seguir.</span><span class="sxs-lookup"><span data-stu-id="65c78-137">Before C# 6, you could initialize dictionaries and other associative containers using the following syntax.</span></span> <span data-ttu-id="65c78-138">Observe que, em vez da sintaxe do indexador, com parênteses e uma atribuição, ele usa um objeto com vários valores:</span><span class="sxs-lookup"><span data-stu-id="65c78-138">Notice that instead of indexer syntax, with parentheses and an assignment, it uses an object with multiple values:</span></span>

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

<span data-ttu-id="65c78-139">Este exemplo de inicializador chama <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> para adicionar os três itens no dicionário.</span><span class="sxs-lookup"><span data-stu-id="65c78-139">This initializer example calls <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> to add the three items into the dictionary.</span></span> <span data-ttu-id="65c78-140">Essas duas maneiras diferentes para inicializar coleções associativas tem um comportamento um pouco diferente devido às chamadas de método que o compilador gera.</span><span class="sxs-lookup"><span data-stu-id="65c78-140">These two different ways to initialize associative collections have slightly different behavior because of the method calls the compiler generates.</span></span> <span data-ttu-id="65c78-141">As duas variantes trabalham com a classe `Dictionary`.</span><span class="sxs-lookup"><span data-stu-id="65c78-141">Both variants work with the `Dictionary` class.</span></span> <span data-ttu-id="65c78-142">Outros tipos podem ser compatíveis apenas com uma ou com outra, dependendo da API pública deles.</span><span class="sxs-lookup"><span data-stu-id="65c78-142">Other types may only support one or the other based on their public API.</span></span>

## <a name="examples"></a><span data-ttu-id="65c78-143">Exemplos</span><span class="sxs-lookup"><span data-stu-id="65c78-143">Examples</span></span>

<span data-ttu-id="65c78-144">O exemplo a seguir combina os conceitos de inicializadores de coleção e objeto.</span><span class="sxs-lookup"><span data-stu-id="65c78-144">The following example combines the concepts of object and collection initializers.</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

<span data-ttu-id="65c78-145">O exemplo a seguir mostra um objeto que implementa <xref:System.Collections.IEnumerable> e contém um método `Add` com vários parâmetros. Ele usa um inicializador de coleção com vários elementos por item na lista que correspondem à assinatura do método `Add`.</span><span class="sxs-lookup"><span data-stu-id="65c78-145">The following example shows an object that implements <xref:System.Collections.IEnumerable> and contains an `Add` method with multiple parameters, It uses a collection initializer with multiple elements per item in the list that correspond to the signature of the `Add` method.</span></span>

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

<span data-ttu-id="65c78-146">Os métodos `Add` podem usar a palavra-chave `params` para obter um número variável de argumentos, como mostrado no seguinte exemplo.</span><span class="sxs-lookup"><span data-stu-id="65c78-146">`Add` methods can use the `params` keyword to take a variable number of arguments, as shown in the following example.</span></span> <span data-ttu-id="65c78-147">Este exemplo também demonstra a implementação personalizada de um indexador para inicializar uma coleção usando índices.</span><span class="sxs-lookup"><span data-stu-id="65c78-147">This example also demonstrates the custom implementation of an indexer to initialize a collection using indexes.</span></span>

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a><span data-ttu-id="65c78-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65c78-148">See also</span></span>

- [<span data-ttu-id="65c78-149">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="65c78-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="65c78-150">LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="65c78-150">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="65c78-151">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="65c78-151">Anonymous Types</span></span>](anonymous-types.md)
