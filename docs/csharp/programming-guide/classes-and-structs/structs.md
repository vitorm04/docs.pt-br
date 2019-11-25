---
title: Structs – Guia de Programação em C#
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 35b39da0b15c41b7b2c7a6567bea5dca3fb430e7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970313"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="a2670-102">Structs (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="a2670-102">Structs (C# Programming Guide)</span></span>

<span data-ttu-id="a2670-103">Structs são definidos usando a palavra-chave [struct](../../language-reference/keywords/struct.md), por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a2670-103">Structs are defined by using the [struct](../../language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#39)]  
  
<span data-ttu-id="a2670-104">Os structs compartilham a maioria da mesma sintaxe que as classes.</span><span class="sxs-lookup"><span data-stu-id="a2670-104">Structs share most of the same syntax as classes.</span></span> <span data-ttu-id="a2670-105">O nome da struct deve ser um [nome do identificador](../inside-a-program/identifier-names.md) válido em C#.</span><span class="sxs-lookup"><span data-stu-id="a2670-105">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="a2670-106">Os structs são mais limitados do que as classes das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="a2670-106">Structs are more limited than classes in the following ways:</span></span>  
  
- <span data-ttu-id="a2670-107">Dentro de uma declaração de struct, os campos não podem ser inicializados, a menos que sejam declarados como const ou estáticos.</span><span class="sxs-lookup"><span data-stu-id="a2670-107">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
- <span data-ttu-id="a2670-108">Um struct não pode declarar um construtor sem padrão (um construtor sem parâmetros) ou um finalizador.</span><span class="sxs-lookup"><span data-stu-id="a2670-108">A struct cannot declare a parameterless constructor (a constructor without parameters) or a finalizer.</span></span>  
- <span data-ttu-id="a2670-109">Os structs são copiados na atribuição.</span><span class="sxs-lookup"><span data-stu-id="a2670-109">Structs are copied on assignment.</span></span> <span data-ttu-id="a2670-110">Quando um struct recebe uma nova variável, todos os dados são copiados e qualquer modificação na nova cópia não altera os dados da cópia original.</span><span class="sxs-lookup"><span data-stu-id="a2670-110">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="a2670-111">É importante se lembrar disso ao trabalhar com coleções de tipos de valor como `Dictionary<string, myStruct>`.</span><span class="sxs-lookup"><span data-stu-id="a2670-111">This is important to remember when working with collections of value types such as `Dictionary<string, myStruct>`.</span></span>  
- <span data-ttu-id="a2670-112">Os structs são tipos de valor, diferentemente das classes, que são tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="a2670-112">Structs are value types, unlike classes, which are reference types.</span></span>  
- <span data-ttu-id="a2670-113">Diferentemente das classes, os structs podem ser instanciados sem usar um operador `new`.</span><span class="sxs-lookup"><span data-stu-id="a2670-113">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
- <span data-ttu-id="a2670-114">Os structs podem declarar construtores que têm parâmetros.</span><span class="sxs-lookup"><span data-stu-id="a2670-114">Structs can declare constructors that have parameters.</span></span>
- <span data-ttu-id="a2670-115">Um struct não pode herdar de outra estrutura ou classe e ele não pode ser a base de uma classe.</span><span class="sxs-lookup"><span data-stu-id="a2670-115">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="a2670-116">Todos os structs herdam diretamente do <xref:System.ValueType>, que herda do <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="a2670-116">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
- <span data-ttu-id="a2670-117">Um struct pode implementar interfaces.</span><span class="sxs-lookup"><span data-stu-id="a2670-117">A struct can implement interfaces.</span></span>
- <span data-ttu-id="a2670-118">Um struct não pode ser `null`e uma variável de struct não pode ser atribuída `null` a menos que a variável seja declarada como um tipo de valor anulável.</span><span class="sxs-lookup"><span data-stu-id="a2670-118">A struct cannot be `null`, and a struct variable cannot be assigned `null` unless the variable is declared as a nullable value type.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a2670-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2670-119">See also</span></span>

- [<span data-ttu-id="a2670-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a2670-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a2670-121">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="a2670-121">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="a2670-122">Classes</span><span class="sxs-lookup"><span data-stu-id="a2670-122">Classes</span></span>](classes.md)
- [<span data-ttu-id="a2670-123">Tipos de valor anuláveis</span><span class="sxs-lookup"><span data-stu-id="a2670-123">Nullable value types</span></span>](../../language-reference/builtin-types/nullable-value-types.md)
- [<span data-ttu-id="a2670-124">Nomes de identificadores</span><span class="sxs-lookup"><span data-stu-id="a2670-124">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="a2670-125">Usando structs</span><span class="sxs-lookup"><span data-stu-id="a2670-125">Using Structs</span></span>](using-structs.md)
- [<span data-ttu-id="a2670-126">Como saber a diferença entre passar uma struct e passar uma referência de classe para um método</span><span class="sxs-lookup"><span data-stu-id="a2670-126">How to know the difference between passing a struct and passing a class reference to a method</span></span>](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
