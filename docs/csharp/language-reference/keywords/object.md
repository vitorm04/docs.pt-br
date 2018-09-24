---
title: object (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
ms.openlocfilehash: b36703828e6027a89297ac88edaf2b55ec18f42e
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46579599"
---
# <a name="object-c-reference"></a><span data-ttu-id="20b49-102">object (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="20b49-102">object (C# Reference)</span></span>

<span data-ttu-id="20b49-103">O tipo `object` é um alias de <xref:System.Object> no .NET.</span><span class="sxs-lookup"><span data-stu-id="20b49-103">The `object` type is an alias for <xref:System.Object> in .NET.</span></span> <span data-ttu-id="20b49-104">No sistema de tipos unificado do C#, todos os tipos, predefinidos e definidos pelo usuário, tipos de referência e tipos de valor, herdam direta ou indiretamente de <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="20b49-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="20b49-105">Você pode atribuir valores de qualquer tipo a variáveis do tipo `object`.</span><span class="sxs-lookup"><span data-stu-id="20b49-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="20b49-106">Quando uma variável de um tipo de valor é convertida para um objeto, ela é chamada de *boxed*.</span><span class="sxs-lookup"><span data-stu-id="20b49-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="20b49-107">Quando uma variável do objeto do tipo é convertida para um tipo de valor, ela é chamada de *unboxed*.</span><span class="sxs-lookup"><span data-stu-id="20b49-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="20b49-108">Para obter mais informações, consulte [Boxing e unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="20b49-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>

## <a name="example"></a><span data-ttu-id="20b49-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="20b49-109">Example</span></span>

<span data-ttu-id="20b49-110">O exemplo a seguir mostra como variáveis do tipo `object` podem aceitar valores de qualquer tipo de dados e como as variáveis do tipo `object` pode usar métodos <xref:System.Object> do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="20b49-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>

[!code-csharp[csrefKeywordsTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#16)]

## <a name="c-language-specification"></a><span data-ttu-id="20b49-111">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="20b49-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="20b49-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20b49-112">See also</span></span>

- [<span data-ttu-id="20b49-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="20b49-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="20b49-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="20b49-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="20b49-115">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="20b49-115">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="20b49-116">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="20b49-116">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="20b49-117">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="20b49-117">Value Types</span></span>](value-types.md)