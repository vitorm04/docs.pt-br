---
title: Structs (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: ffb5b8da6c72056620cf890f38af4e7a8116ab3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322982"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="40247-102">Structs (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="40247-102">Structs (C# Programming Guide)</span></span>
<span data-ttu-id="40247-103">Structs são definidos usando a palavra-chave [struct](../../../csharp/language-reference/keywords/struct.md), por exemplo:</span><span class="sxs-lookup"><span data-stu-id="40247-103">Structs are defined by using the [struct](../../../csharp/language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 <span data-ttu-id="40247-104">Na maioria das vezes, os structs compartilham a mesma sintaxe das classes, embora os structs sejam mais limitados que as classes:</span><span class="sxs-lookup"><span data-stu-id="40247-104">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>  
  
-   <span data-ttu-id="40247-105">Dentro de uma declaração de struct, os campos não podem ser inicializados, a menos que sejam declarados como const ou estáticos.</span><span class="sxs-lookup"><span data-stu-id="40247-105">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
  
-   <span data-ttu-id="40247-106">Um struct não pode declarar um construtor padrão (um construtor sem parâmetros) ou um finalizador.</span><span class="sxs-lookup"><span data-stu-id="40247-106">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
  
-   <span data-ttu-id="40247-107">Os structs são copiados na atribuição.</span><span class="sxs-lookup"><span data-stu-id="40247-107">Structs are copied on assignment.</span></span> <span data-ttu-id="40247-108">Quando um struct recebe uma nova variável, todos os dados são copiados e qualquer modificação na nova cópia não altera os dados da cópia original.</span><span class="sxs-lookup"><span data-stu-id="40247-108">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="40247-109">É importante se lembrar disso ao trabalhar com coleções de tipos de valor como dicionário\<string, myStruct>.</span><span class="sxs-lookup"><span data-stu-id="40247-109">This is important to remember when working with collections of value types such as Dictionary\<string, myStruct>.</span></span>  
  
-   <span data-ttu-id="40247-110">Structs são tipos de valor e classes são tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="40247-110">Structs are value types and classes are reference types.</span></span>  
  
-   <span data-ttu-id="40247-111">Diferentemente das classes, os structs podem ser instanciados sem usar um operador `new`.</span><span class="sxs-lookup"><span data-stu-id="40247-111">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
  
-   <span data-ttu-id="40247-112">Os structs podem declarar construtores que têm parâmetros.</span><span class="sxs-lookup"><span data-stu-id="40247-112">Structs can declare constructors that have parameters.</span></span>  
  
-   <span data-ttu-id="40247-113">Um struct não pode herdar de outra estrutura ou classe e ele não pode ser a base de uma classe.</span><span class="sxs-lookup"><span data-stu-id="40247-113">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="40247-114">Todos os structs herdam diretamente do `System.ValueType`, que herda do `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="40247-114">All structs inherit directly from `System.ValueType`, which inherits from `System.Object`.</span></span>  
  
-   <span data-ttu-id="40247-115">Um struct pode implementar interfaces.</span><span class="sxs-lookup"><span data-stu-id="40247-115">A struct can implement interfaces.</span></span>  
  
-   <span data-ttu-id="40247-116">Um struct pode ser usado como um tipo que permite valor nulo e pode receber um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="40247-116">A struct can be used as a nullable type and can be assigned a null value.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="40247-117">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="40247-117">Related Sections</span></span>  
 <span data-ttu-id="40247-118">Para saber mais:</span><span class="sxs-lookup"><span data-stu-id="40247-118">For more information:</span></span>  
  
-   [<span data-ttu-id="40247-119">Usando structs</span><span class="sxs-lookup"><span data-stu-id="40247-119">Using Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [<span data-ttu-id="40247-120">Construtores</span><span class="sxs-lookup"><span data-stu-id="40247-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [<span data-ttu-id="40247-121">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="40247-121">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [<span data-ttu-id="40247-122">Como saber a diferença entre passar um struct e passar uma referência de classe para um método</span><span class="sxs-lookup"><span data-stu-id="40247-122">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [<span data-ttu-id="40247-123">Como implementar conversões definidas pelo usuário entre structs</span><span class="sxs-lookup"><span data-stu-id="40247-123">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a><span data-ttu-id="40247-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40247-124">See Also</span></span>  
 [<span data-ttu-id="40247-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="40247-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="40247-126">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="40247-126">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="40247-127">Classes</span><span class="sxs-lookup"><span data-stu-id="40247-127">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)
