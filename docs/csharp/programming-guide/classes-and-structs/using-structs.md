---
title: "Usando structs (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
caps.latest.revision: 28
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 67fa4f764e6e40041e4b8e37eccbd1adb2b509d3
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="using-structs-c-programming-guide"></a><span data-ttu-id="07649-102">Usando structs (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="07649-102">Using Structs (C# Programming Guide)</span></span>
<span data-ttu-id="07649-103">O tipo `struct` é adequado para representar objetos leves como `Point`, `Rectangle` e `Color`.</span><span class="sxs-lookup"><span data-stu-id="07649-103">The `struct` type is suitable for representing lightweight objects such as `Point`, `Rectangle`, and `Color`.</span></span> <span data-ttu-id="07649-104">Embora seja conveniente representar um ponto como uma [classe](../../../csharp/language-reference/keywords/class.md) com [Propriedades Auto-implementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), um [struct](../../../csharp/language-reference/keywords/struct.md) pode ser mais eficiente em alguns cenários.</span><span class="sxs-lookup"><span data-stu-id="07649-104">Although it is just as convenient to represent a point as a [class](../../../csharp/language-reference/keywords/class.md) with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), a [struct](../../../csharp/language-reference/keywords/struct.md) might be more efficient in some scenarios.</span></span> <span data-ttu-id="07649-105">Por exemplo, se você declarar uma matriz de 1000 objetos `Point`, alocará memória adicional para referenciar cada objeto, nesse caso, um struct será mais barato.</span><span class="sxs-lookup"><span data-stu-id="07649-105">For example, if you declare an array of 1000 `Point` objects, you will allocate additional memory for referencing each object; in this case, a struct would be less expensive.</span></span> <span data-ttu-id="07649-106">Como o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] contém um objeto chamado <xref:System.Drawing.Point>, o struct neste exemplo é chamado “CoOrds”.</span><span class="sxs-lookup"><span data-stu-id="07649-106">Because the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] contains an object called <xref:System.Drawing.Point>, the struct in this example is named "CoOrds" instead.</span></span>  
  
 <span data-ttu-id="07649-107">[!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="07649-107">[!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]</span></span>  
  
 <span data-ttu-id="07649-108">É um erro ao definir um construtor (sem parâmetros) padrão para um struct.</span><span class="sxs-lookup"><span data-stu-id="07649-108">It is an error to define a default (parameterless) constructor for a struct.</span></span> <span data-ttu-id="07649-109">Também é um erro ao inicializar um campo de instância em um corpo de struct.</span><span class="sxs-lookup"><span data-stu-id="07649-109">It is also an error to initialize an instance field in a struct body.</span></span> <span data-ttu-id="07649-110">Você pode inicializar membros de struct apenas usando um construtor com parâmetros ou acessando os membros individualmente depois que a estrutura é declarada.</span><span class="sxs-lookup"><span data-stu-id="07649-110">You can initialize struct members only by using a parameterized constructor or by accessing the members individually after the struct is declared.</span></span> <span data-ttu-id="07649-111">Todos os membros particulares ou inacessíveis podem ser inicializados somente em um construtor.</span><span class="sxs-lookup"><span data-stu-id="07649-111">Any private or otherwise inaccessible members can be initialized only in a constructor.</span></span>  
  
 <span data-ttu-id="07649-112">Quando você cria um objeto de struct usando o operador [new](../../../csharp/language-reference/keywords/new.md), ele é criado e o construtor apropriado é chamado.</span><span class="sxs-lookup"><span data-stu-id="07649-112">When you create a struct object using the [new](../../../csharp/language-reference/keywords/new.md) operator, it gets created and the appropriate constructor is called.</span></span> <span data-ttu-id="07649-113">Diferentemente das classes, os structs podem ser instanciados sem usar o operador `new`.</span><span class="sxs-lookup"><span data-stu-id="07649-113">Unlike classes, structs can be instantiated without using the `new` operator.</span></span> <span data-ttu-id="07649-114">Nesse caso, não há nenhuma chamada do construtor, o que torna a alocação mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="07649-114">In such a case, there is no constructor call, which makes the allocation more efficient.</span></span> <span data-ttu-id="07649-115">No entanto, os campos permanecerão não atribuídos e o objeto não poderá ser usado até que todos os campos sejam inicializados.</span><span class="sxs-lookup"><span data-stu-id="07649-115">However, the fields will remain unassigned and the object cannot be used until all of the fields are initialized.</span></span>  
  
 <span data-ttu-id="07649-116">Quando um struct contém um tipo de referência como um membro, o construtor padrão do membro deve ser invocado explicitamente, caso contrário, o membro permanece não atribuído e o struct não pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="07649-116">When a struct contains a reference type as a member, the default constructor of the member must be invoked explicitly, otherwise the member remains unassigned and the struct cannot be used.</span></span> <span data-ttu-id="07649-117">(Isso resulta no erro do compilador CS0171.)</span><span class="sxs-lookup"><span data-stu-id="07649-117">(This results in compiler error CS0171.)</span></span>  
  
 <span data-ttu-id="07649-118">Não há nenhuma herança para structs como há para classes.</span><span class="sxs-lookup"><span data-stu-id="07649-118">There is no inheritance for structs as there is for classes.</span></span> <span data-ttu-id="07649-119">Um struct não pode herdar de outra estrutura ou classe e ele não pode ser a base de uma classe.</span><span class="sxs-lookup"><span data-stu-id="07649-119">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="07649-120">No entanto, os structs herdam da classe base <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="07649-120">Structs, however, inherit from the base class <xref:System.Object>.</span></span> <span data-ttu-id="07649-121">Um struct pode implementar interfaces e ele faz isso exatamente como as classes.</span><span class="sxs-lookup"><span data-stu-id="07649-121">A struct can implement interfaces, and it does that exactly as classes do.</span></span>  
  
 <span data-ttu-id="07649-122">Você não pode declarar uma classe usando a palavra-chave `struct`.</span><span class="sxs-lookup"><span data-stu-id="07649-122">You cannot declare a class using the keyword `struct`.</span></span> <span data-ttu-id="07649-123">No C#, as classes e os structs são semanticamente diferentes.</span><span class="sxs-lookup"><span data-stu-id="07649-123">In C#, classes and structs are semantically different.</span></span> <span data-ttu-id="07649-124">Um struct é um tipo de valor, enquanto uma classe é um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="07649-124">A struct is a value type, while a class is a reference type.</span></span> <span data-ttu-id="07649-125">Para obter mais informações, consulte [Value Types](../../../csharp/language-reference/keywords/value-types.md) (Tipos de Valor).</span><span class="sxs-lookup"><span data-stu-id="07649-125">For more information, see [Value Types](../../../csharp/language-reference/keywords/value-types.md).</span></span>  
  
 <span data-ttu-id="07649-126">A menos que você precise de semântica de tipo de referência, uma pequena classe pode ser tratada com mais eficiência pelo sistema se você declará-la como um struct em vez disso.</span><span class="sxs-lookup"><span data-stu-id="07649-126">Unless you need reference-type semantics, a small class may be more efficiently handled by the system if you declare it as a struct instead.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="07649-127">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="07649-127">Example 1</span></span>  
  
### <a name="description"></a><span data-ttu-id="07649-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="07649-128">Description</span></span>  
 <span data-ttu-id="07649-129">Este exemplo demonstra a inicialização de `struct` usando construtores parametrizados e padrão.</span><span class="sxs-lookup"><span data-stu-id="07649-129">This example demonstrates `struct` initialization using both default and parameterized constructors.</span></span>  
  
### <a name="code"></a><span data-ttu-id="07649-130">Código</span><span class="sxs-lookup"><span data-stu-id="07649-130">Code</span></span>  
 <span data-ttu-id="07649-131">[!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="07649-131">[!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]</span></span>  
  
 <span data-ttu-id="07649-132">[!code-cs[csProgGuideObjects#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="07649-132">[!code-cs[csProgGuideObjects#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_2.cs)]</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="07649-133">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="07649-133">Example 2</span></span>  
  
### <a name="description"></a><span data-ttu-id="07649-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="07649-134">Description</span></span>  
 <span data-ttu-id="07649-135">Este exemplo demonstra um recurso que é exclusivo para struct.</span><span class="sxs-lookup"><span data-stu-id="07649-135">This example demonstrates a feature that is unique to structs.</span></span> <span data-ttu-id="07649-136">Ele cria um objeto CoOrds sem usar o operador `new`.</span><span class="sxs-lookup"><span data-stu-id="07649-136">It creates a CoOrds object without using the `new` operator.</span></span> <span data-ttu-id="07649-137">Se você substituir a palavra `struct` pela palavra `class`, o programa não compilará.</span><span class="sxs-lookup"><span data-stu-id="07649-137">If you replace the word `struct` with the word `class`, the program will not compile.</span></span>  
  
### <a name="code"></a><span data-ttu-id="07649-138">Código</span><span class="sxs-lookup"><span data-stu-id="07649-138">Code</span></span>  
 <span data-ttu-id="07649-139">[!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="07649-139">[!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]</span></span>  
  
 <span data-ttu-id="07649-140">[!code-cs[csProgGuideObjects#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="07649-140">[!code-cs[csProgGuideObjects#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07649-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07649-141">See Also</span></span>  
 <span data-ttu-id="07649-142">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="07649-142">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="07649-143">[Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="07649-143">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 [<span data-ttu-id="07649-144">Estruturas</span><span class="sxs-lookup"><span data-stu-id="07649-144">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)

