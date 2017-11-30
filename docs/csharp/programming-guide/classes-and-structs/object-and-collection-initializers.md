---
title: "Inicializadores de objeto e coleção (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7445a2919baaa477b4611c4c5ee5a0031539ca30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="25f9c-102">Inicializadores de objeto e coleção (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="25f9c-102">Object and Collection Initializers (C# Programming Guide)</span></span>
<span data-ttu-id="25f9c-103">Os inicializadores de objeto permitem atribuir valores a quaisquer campos ou propriedades acessíveis de um objeto na hora de criação sem que seja necessário invocar um construtor seguido por linhas de instruções de atribuição.</span><span class="sxs-lookup"><span data-stu-id="25f9c-103">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="25f9c-104">A sintaxe do inicializador de objeto permite especificar argumentos para um construtor ou omitir os argumentos (e a sintaxe de parênteses).</span><span class="sxs-lookup"><span data-stu-id="25f9c-104">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="25f9c-105">O exemplo a seguir mostra como usar um inicializador de objeto com um tipo nomeado `Cat` e como invocar o construtor padrão.</span><span class="sxs-lookup"><span data-stu-id="25f9c-105">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the default constructor.</span></span> <span data-ttu-id="25f9c-106">Observe o uso de propriedades autoimplementadas na classe `Cat`.</span><span class="sxs-lookup"><span data-stu-id="25f9c-106">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="25f9c-107">Para obter mais informações, consulte [Propriedades autoimplementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="25f9c-107">For more information, see [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-csharp[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)] 
 
<span data-ttu-id="25f9c-108">A sintaxe de inicializadores de objeto permite que você crie uma instância e, depois que ele atribui o objeto recentemente criado, com suas propriedades atribuídos, a variável na atribuição.</span><span class="sxs-lookup"><span data-stu-id="25f9c-108">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>
  
## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="25f9c-109">Inicializadores de objeto com tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="25f9c-109">Object Initializers with anonymous types</span></span>  
 <span data-ttu-id="25f9c-110">Embora inicializadores de objetos possam ser usados em qualquer contexto, eles são especialmente úteis em expressões de consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25f9c-110">Although object initializers can be used in any context, they are especially useful in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="25f9c-111">Expressões de consulta fazem uso frequente de [tipos anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), que podem ser inicializados somente usando um inicializador de objeto, como mostrado na declaração a seguir.</span><span class="sxs-lookup"><span data-stu-id="25f9c-111">Query expressions make frequent use of [anonymous types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 <span data-ttu-id="25f9c-112">Os tipos anônimos habilitam a cláusula `select` em uma expressão de consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] a transformar objetos da sequência original em objetos cujo valor e forma podem diferir dos originais.</span><span class="sxs-lookup"><span data-stu-id="25f9c-112">Anonymous types enable the `select` clause in a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="25f9c-113">Isso será útil se você desejar armazenar apenas uma parte das informações de cada objeto em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="25f9c-113">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="25f9c-114">No exemplo a seguir, suponha que um objeto de produto (`p`) contenha vários campos e métodos e que você esteja apenas interessado em criar uma sequência de objetos que contenha o nome do produto e o preço unitário.</span><span class="sxs-lookup"><span data-stu-id="25f9c-114">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 <span data-ttu-id="25f9c-115">Quando essa consulta for executada, a variável `productInfos` conterá uma sequência de objetos que podem ser acessados em uma instrução `foreach` como mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="25f9c-115">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 <span data-ttu-id="25f9c-116">Cada objeto no novo tipo anônimo tem duas propriedades públicas que recebem os mesmos nomes que as propriedades ou os campos no objeto original.</span><span class="sxs-lookup"><span data-stu-id="25f9c-116">Each object in the new anonymous type has two public properties which receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="25f9c-117">Você também poderá renomear um campo quando estiver criando um tipo anônimo; o exemplo a seguir renomeia o campo `UnitPrice` como `Price`.</span><span class="sxs-lookup"><span data-stu-id="25f9c-117">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="object-initializers-with-nullable-types"></a><span data-ttu-id="25f9c-118">Inicializadores de objeto com tipos anuláveis</span><span class="sxs-lookup"><span data-stu-id="25f9c-118">Object initializers with nullable types</span></span>  
 <span data-ttu-id="25f9c-119">É um erro de tempo de compilação usar um inicializador de objeto com um struct anulável.</span><span class="sxs-lookup"><span data-stu-id="25f9c-119">It is a compile-time error to use an object initializer with a nullable struct.</span></span>  
  
## <a name="collection-initializers"></a><span data-ttu-id="25f9c-120">Inicializadores de coleção</span><span class="sxs-lookup"><span data-stu-id="25f9c-120">Collection initializers</span></span>  
 <span data-ttu-id="25f9c-121">Os inicializadores de coleção permitem especificar um ou mais inicializadores de elemento quando você inicializa um tipo de coleção que implementa <xref:System.Collections.IEnumerable> e tem `Add` com a assinatura apropriada como um método de instância ou um método de extensão.</span><span class="sxs-lookup"><span data-stu-id="25f9c-121">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="25f9c-122">Os inicializadores de elemento podem ser um valor simples, uma expressão ou um inicializador de objeto.</span><span class="sxs-lookup"><span data-stu-id="25f9c-122">The element initializers can be a simple value, an expression or an object initializer.</span></span> <span data-ttu-id="25f9c-123">Ao usar um inicializador de coleção, não é necessário especificar várias chamadas para o método `Add` da classe em seu código-fonte; o compilador adiciona as chamadas.</span><span class="sxs-lookup"><span data-stu-id="25f9c-123">By using a collection initializer you do not have to specify multiple calls to the `Add` method of the class in your source code; the compiler adds the calls.</span></span>  
  
 <span data-ttu-id="25f9c-124">Os exemplos a seguir mostram dois inicializadores de coleção simples:</span><span class="sxs-lookup"><span data-stu-id="25f9c-124">The following examples shows two simple collection initializers:</span></span>  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 <span data-ttu-id="25f9c-125">O inicializador de coleção a seguir usa inicializadores de objeto para inicializar objetos da classe `Cat` definida em um exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="25f9c-125">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="25f9c-126">Observe que os inicializadores de objeto individuais são envolvidos por chaves e separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="25f9c-126">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 <span data-ttu-id="25f9c-127">Você poderá especificar [nulo](../../../csharp/language-reference/keywords/null.md) como um elemento em um inicializador de coleção se o método `Add` da coleção permitir.</span><span class="sxs-lookup"><span data-stu-id="25f9c-127">You can specify [null](../../../csharp/language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 <span data-ttu-id="25f9c-128">É possível especificar elementos indexados se a coleção der suporte a indexação.</span><span class="sxs-lookup"><span data-stu-id="25f9c-128">You can specify indexed elements if the collection supports indexing.</span></span>  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="example"></a><span data-ttu-id="25f9c-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="25f9c-129">Example</span></span>  
 [!code-csharp[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="25f9c-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25f9c-130">See Also</span></span>  
 [<span data-ttu-id="25f9c-131">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="25f9c-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="25f9c-132">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="25f9c-132">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="25f9c-133">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="25f9c-133">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
