---
title: "Structs (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ce12f402c0748ea6729c82e3f188c0a58f63d628
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="bf3df-102">Structs (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="bf3df-102">Structs (C# Programming Guide)</span></span>
<span data-ttu-id="bf3df-103">Structs são definidos usando a palavra-chave [struct](../../../csharp/language-reference/keywords/struct.md), por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bf3df-103">Structs are defined by using the [struct](../../../csharp/language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 <span data-ttu-id="bf3df-104">[!code-cs[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="bf3df-104">[!code-cs[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]</span></span>  
  
 <span data-ttu-id="bf3df-105">Na maioria das vezes, os structs compartilham a mesma sintaxe das classes, embora os structs sejam mais limitados que as classes:</span><span class="sxs-lookup"><span data-stu-id="bf3df-105">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>  
  
-   <span data-ttu-id="bf3df-106">Dentro de uma declaração de struct, os campos não podem ser inicializados, a menos que sejam declarados como const ou estáticos.</span><span class="sxs-lookup"><span data-stu-id="bf3df-106">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
  
-   <span data-ttu-id="bf3df-107">Um struct não pode declarar um construtor padrão (um construtor sem parâmetros) ou um finalizador.</span><span class="sxs-lookup"><span data-stu-id="bf3df-107">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
  
-   <span data-ttu-id="bf3df-108">Os structs são copiados na atribuição.</span><span class="sxs-lookup"><span data-stu-id="bf3df-108">Structs are copied on assignment.</span></span> <span data-ttu-id="bf3df-109">Quando um struct recebe uma nova variável, todos os dados são copiados e qualquer modificação na nova cópia não altera os dados da cópia original.</span><span class="sxs-lookup"><span data-stu-id="bf3df-109">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="bf3df-110">É importante se lembrar disso ao trabalhar com coleções de tipos de valor como dicionário\<string, myStruct>.</span><span class="sxs-lookup"><span data-stu-id="bf3df-110">This is important to remember when working with collections of value types such as Dictionary\<string, myStruct>.</span></span>  
  
-   <span data-ttu-id="bf3df-111">Structs são tipos de valor e classes são tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="bf3df-111">Structs are value types and classes are reference types.</span></span>  
  
-   <span data-ttu-id="bf3df-112">Diferentemente das classes, os structs podem ser instanciados sem usar um operador `new`.</span><span class="sxs-lookup"><span data-stu-id="bf3df-112">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
  
-   <span data-ttu-id="bf3df-113">Os structs podem declarar construtores que têm parâmetros.</span><span class="sxs-lookup"><span data-stu-id="bf3df-113">Structs can declare constructors that have parameters.</span></span>  
  
-   <span data-ttu-id="bf3df-114">Um struct não pode herdar de outra estrutura ou classe e ele não pode ser a base de uma classe.</span><span class="sxs-lookup"><span data-stu-id="bf3df-114">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="bf3df-115">Todos os structs herdam diretamente do `System.ValueType`, que herda do `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="bf3df-115">All structs inherit directly from `System.ValueType`, which inherits from `System.Object`.</span></span>  
  
-   <span data-ttu-id="bf3df-116">Um struct pode implementar interfaces.</span><span class="sxs-lookup"><span data-stu-id="bf3df-116">A struct can implement interfaces.</span></span>  
  
-   <span data-ttu-id="bf3df-117">Um struct pode ser usado como um tipo que permite valor nulo e pode receber um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bf3df-117">A struct can be used as a nullable type and can be assigned a null value.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bf3df-118">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="bf3df-118">Related Sections</span></span>  
 <span data-ttu-id="bf3df-119">Para saber mais:</span><span class="sxs-lookup"><span data-stu-id="bf3df-119">For more information:</span></span>  
  
-   [<span data-ttu-id="bf3df-120">Usando structs</span><span class="sxs-lookup"><span data-stu-id="bf3df-120">Using Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [<span data-ttu-id="bf3df-121">Construtores</span><span class="sxs-lookup"><span data-stu-id="bf3df-121">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [<span data-ttu-id="bf3df-122">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="bf3df-122">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [<span data-ttu-id="bf3df-123">Como saber a diferença entre passar um struct e passar uma referência de classe para um método</span><span class="sxs-lookup"><span data-stu-id="bf3df-123">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [<span data-ttu-id="bf3df-124">Como implementar conversões definidas pelo usuário entre structs</span><span class="sxs-lookup"><span data-stu-id="bf3df-124">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a><span data-ttu-id="bf3df-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf3df-125">See Also</span></span>  
 <span data-ttu-id="bf3df-126">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="bf3df-126">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="bf3df-127">[Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="bf3df-127">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 [<span data-ttu-id="bf3df-128">Classes</span><span class="sxs-lookup"><span data-stu-id="bf3df-128">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)

