---
title: Operador new (Referência em C#)
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 362217b247bd2ab7a2eec2f86cbaaf1a0652a3ad
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44275204"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="03dba-102">Operador new (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="03dba-102">new operator (C# Reference)</span></span>

<span data-ttu-id="03dba-103">Usado para criar objetos e invocar construtores.</span><span class="sxs-lookup"><span data-stu-id="03dba-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="03dba-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="03dba-104">For example:</span></span>

```csharp
Class1 obj  = new Class1();
```

<span data-ttu-id="03dba-105">Ele também é usado para criar instâncias de tipos anônimos:</span><span class="sxs-lookup"><span data-stu-id="03dba-105">It is also used to create instances of anonymous types:</span></span>

```csharp
var query = from cust in customers
            select new { Name = cust.Name, Address = cust.PrimaryAddress };
```

<span data-ttu-id="03dba-106">O operador `new` também é usado para invocar o construtor padrão para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="03dba-106">The `new` operator is also used to invoke the default constructor for value types.</span></span> <span data-ttu-id="03dba-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="03dba-107">For example:</span></span>

```csharp
int i = new int();
```

<span data-ttu-id="03dba-108">Na instrução anterior, `i` é inicializado como `0`, que é o valor padrão do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="03dba-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="03dba-109">A instrução tem o mesmo efeito que o seguinte:</span><span class="sxs-lookup"><span data-stu-id="03dba-109">The statement has the same effect as the following:</span></span>

```csharp
int i = 0;
```

<span data-ttu-id="03dba-110">Para ver uma lista completa dos valores padrão, consulte [Tabela de valores padrão](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="03dba-110">For a complete list of default values, see [Default Values Table](default-values-table.md).</span></span>

<span data-ttu-id="03dba-111">Lembre-se de que é um erro declarar um construtor padrão para um [struct](struct.md), porque cada tipo de valor tem implicitamente um construtor padrão público.</span><span class="sxs-lookup"><span data-stu-id="03dba-111">Remember that it is an error to declare a default constructor for a [struct](struct.md) because every value type implicitly has a public default constructor.</span></span> <span data-ttu-id="03dba-112">É possível declarar construtores parametrizados em um tipo de struct para definir seus valores iniciais, mas isso só é necessário se valores diferentes do padrão forem necessários.</span><span class="sxs-lookup"><span data-stu-id="03dba-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>

<span data-ttu-id="03dba-113">Tanto os objetos de tipo de valor, como structs, quanto os objetos de tipo de referência, como as classes, são destruídos automaticamente, mas os objetos de tipo de valor são destruídos quando o contexto que os contém é destruído, enquanto que os objetos de tipo de referência são destruídos pelo coletor de lixo em um momento não especificado, depois que a última referência a eles é removida.</span><span class="sxs-lookup"><span data-stu-id="03dba-113">Both value-type objects such as structs and reference-type objects such as classes are destroyed automatically, but value-type objects are destroyed when their containing context is destroyed, whereas reference-type objects are destroyed by the garbage collector at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="03dba-114">Para tipos que contêm recursos, como identificadores de arquivos ou conexões de rede, é desejável empregar limpeza determinística para garantir que os recursos que eles contêm sejam liberados assim que possível.</span><span class="sxs-lookup"><span data-stu-id="03dba-114">For types that contain resources such as file handles, or network connections, it is desirable to employ deterministic cleanup to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="03dba-115">Para obter mais informações, consulte [Instrução using](using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="03dba-115">For more information, see [using Statement](using-statement.md).</span></span>

<span data-ttu-id="03dba-116">O operador `new` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="03dba-116">The `new` operator cannot be overloaded.</span></span>

<span data-ttu-id="03dba-117">Se o operador `new` não conseguir alocar memória, ele gerará a exceção <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="03dba-117">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>

## <a name="example"></a><span data-ttu-id="03dba-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="03dba-118">Example</span></span>

<span data-ttu-id="03dba-119">No exemplo a seguir, um objeto `struct` e um objeto de classe são criados e inicializados usando o operador `new` e, em seguida, valores atribuídos.</span><span class="sxs-lookup"><span data-stu-id="03dba-119">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="03dba-120">Os valores padrão e atribuídos são exibidos.</span><span class="sxs-lookup"><span data-stu-id="03dba-120">The default and the assigned values are displayed.</span></span>

[!code-csharp[csrefKeywordsOperator#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#7)]

<span data-ttu-id="03dba-121">Observe, no exemplo, que o valor padrão de uma cadeia de caracteres é `null`.</span><span class="sxs-lookup"><span data-stu-id="03dba-121">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="03dba-122">Portanto, ele não é exibido.</span><span class="sxs-lookup"><span data-stu-id="03dba-122">Therefore, it is not displayed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="03dba-123">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="03dba-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="03dba-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03dba-124">See also</span></span>

- [<span data-ttu-id="03dba-125">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="03dba-125">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="03dba-126">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="03dba-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="03dba-127">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="03dba-127">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="03dba-128">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="03dba-128">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="03dba-129">new</span><span class="sxs-lookup"><span data-stu-id="03dba-129">new</span></span>](new.md)
- [<span data-ttu-id="03dba-130">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="03dba-130">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)