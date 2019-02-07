---
title: Structs – Guia de Programação em C#
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 609169d4624802f679f9661b7aa0596403cc48e7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261606"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="c5d22-102">Structs (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="c5d22-102">Structs (C# Programming Guide)</span></span>

<span data-ttu-id="c5d22-103">Structs são definidos usando a palavra-chave [struct](../../language-reference/keywords/struct.md), por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c5d22-103">Structs are defined by using the [struct](../../language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
[!code-csharp[csProgGuideObjects#39](./codesnippet/CSharp/structs_1.cs)]  
  
<span data-ttu-id="c5d22-104">Os structs compartilham a maioria da mesma sintaxe que as classes.</span><span class="sxs-lookup"><span data-stu-id="c5d22-104">Structs share most of the same syntax as classes.</span></span> <span data-ttu-id="c5d22-105">O nome da struct deve ser um [nome do identificador](../inside-a-program/identifier-names.md) válido em C#.</span><span class="sxs-lookup"><span data-stu-id="c5d22-105">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="c5d22-106">Os structs são mais limitados do que as classes das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="c5d22-106">Structs are more limited than classes in the following ways:</span></span>  
  
- <span data-ttu-id="c5d22-107">Dentro de uma declaração de struct, os campos não podem ser inicializados, a menos que sejam declarados como const ou estáticos.</span><span class="sxs-lookup"><span data-stu-id="c5d22-107">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
- <span data-ttu-id="c5d22-108">Um struct não pode declarar um construtor padrão (um construtor sem parâmetros) ou um finalizador.</span><span class="sxs-lookup"><span data-stu-id="c5d22-108">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
- <span data-ttu-id="c5d22-109">Os structs são copiados na atribuição.</span><span class="sxs-lookup"><span data-stu-id="c5d22-109">Structs are copied on assignment.</span></span> <span data-ttu-id="c5d22-110">Quando um struct recebe uma nova variável, todos os dados são copiados e qualquer modificação na nova cópia não altera os dados da cópia original.</span><span class="sxs-lookup"><span data-stu-id="c5d22-110">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="c5d22-111">É importante se lembrar disso ao trabalhar com coleções de tipos de valor como `Dictionary<string, myStruct>`.</span><span class="sxs-lookup"><span data-stu-id="c5d22-111">This is important to remember when working with collections of value types such as `Dictionary<string, myStruct>`.</span></span>  
- <span data-ttu-id="c5d22-112">Os structs são tipos de valor, diferentemente das classes, que são tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="c5d22-112">Structs are value types, unlike classes, which are reference types.</span></span>  
- <span data-ttu-id="c5d22-113">Diferentemente das classes, os structs podem ser instanciados sem usar um operador `new`.</span><span class="sxs-lookup"><span data-stu-id="c5d22-113">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
- <span data-ttu-id="c5d22-114">Os structs podem declarar construtores que têm parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c5d22-114">Structs can declare constructors that have parameters.</span></span> 
- <span data-ttu-id="c5d22-115">Um struct não pode herdar de outra estrutura ou classe e ele não pode ser a base de uma classe.</span><span class="sxs-lookup"><span data-stu-id="c5d22-115">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="c5d22-116">Todos os structs herdam diretamente do <xref:System.ValueType>, que herda do <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="c5d22-116">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
- <span data-ttu-id="c5d22-117">Um struct pode implementar interfaces.</span><span class="sxs-lookup"><span data-stu-id="c5d22-117">A struct can implement interfaces.</span></span> 
- <span data-ttu-id="c5d22-118">Um struct não pode ser `null`, e uma variável de struct não pode receber `null`, a menos que a variável seja declarada como um tipo que permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="c5d22-118">A struct cannot be `null`, and a struct variable cannot be assigned `null` unless the variable is declared as a nullable type.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="c5d22-119">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="c5d22-119">Related sections</span></span>  

<span data-ttu-id="c5d22-120">Para saber mais:</span><span class="sxs-lookup"><span data-stu-id="c5d22-120">For more information:</span></span>  
  
- [<span data-ttu-id="c5d22-121">Usando structs</span><span class="sxs-lookup"><span data-stu-id="c5d22-121">Using Structs</span></span>](using-structs.md)
- [<span data-ttu-id="c5d22-122">Construtores</span><span class="sxs-lookup"><span data-stu-id="c5d22-122">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="c5d22-123">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="c5d22-123">Nullable Types</span></span>](../nullable-types/index.md)
- [<span data-ttu-id="c5d22-124">Como: saber a diferença entre passar um struct e passar uma referência de classe para um método</span><span class="sxs-lookup"><span data-stu-id="c5d22-124">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
- [<span data-ttu-id="c5d22-125">Como: implementar conversões definidas pelo usuário entre structs</span><span class="sxs-lookup"><span data-stu-id="c5d22-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

## <a name="see-also"></a><span data-ttu-id="c5d22-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5d22-126">See also</span></span>

- [<span data-ttu-id="c5d22-127">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c5d22-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c5d22-128">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="c5d22-128">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="c5d22-129">Classes</span><span class="sxs-lookup"><span data-stu-id="c5d22-129">Classes</span></span>](classes.md)
- [<span data-ttu-id="c5d22-130">Nomes de identificadores</span><span class="sxs-lookup"><span data-stu-id="c5d22-130">Identifier names</span></span>](../inside-a-program/identifier-names.md)
