---
title: Tipos de referência – Referência em C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: 4b3b1d5b27c3f6a88ce752243ab2d1389b168f0e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634054"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="a7d56-102">Tipos de referência (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="a7d56-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="a7d56-103">Há dois tipos em C#: tipos de referência e valor.</span><span class="sxs-lookup"><span data-stu-id="a7d56-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="a7d56-104">Variáveis de tipos de referência armazenam referências em seus dados (objetos) enquanto que variáveis de tipos de valor contém diretamente seus dados.</span><span class="sxs-lookup"><span data-stu-id="a7d56-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="a7d56-105">Com tipos de referência, duas variáveis podem fazer referência ao mesmo objeto; portanto, operações em uma variável podem afetar o objeto referenciado pela outra variável.</span><span class="sxs-lookup"><span data-stu-id="a7d56-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="a7d56-106">Com tipos de valor, cada variável tem sua própria cópia dos dados e as operações em uma variável não podem afetar a outra (exceto no caso das variáveis de parâmetros in, ref e out. Confira o modificador de parâmetro [in](in-parameter-modifier.md), [ref](ref.md) e [out](out-parameter-modifier.md)).</span><span class="sxs-lookup"><span data-stu-id="a7d56-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="a7d56-107">As seguintes palavras-chaves são usadas para declarar tipos de referência:</span><span class="sxs-lookup"><span data-stu-id="a7d56-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="a7d56-108">class</span><span class="sxs-lookup"><span data-stu-id="a7d56-108">class</span></span>](class.md)

- [<span data-ttu-id="a7d56-109">interface</span><span class="sxs-lookup"><span data-stu-id="a7d56-109">interface</span></span>](interface.md)

- [<span data-ttu-id="a7d56-110">delegate</span><span class="sxs-lookup"><span data-stu-id="a7d56-110">delegate</span></span>](delegate.md)

 <span data-ttu-id="a7d56-111">O C# também oferece os seguintes tipos de referência internos:</span><span class="sxs-lookup"><span data-stu-id="a7d56-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="a7d56-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="a7d56-112">dynamic</span></span>](dynamic.md)

- [<span data-ttu-id="a7d56-113">object</span><span class="sxs-lookup"><span data-stu-id="a7d56-113">object</span></span>](object.md)

- [<span data-ttu-id="a7d56-114">string</span><span class="sxs-lookup"><span data-stu-id="a7d56-114">string</span></span>](string.md)

## <a name="see-also"></a><span data-ttu-id="a7d56-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7d56-115">See also</span></span>

- [<span data-ttu-id="a7d56-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a7d56-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="a7d56-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a7d56-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a7d56-118">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="a7d56-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a7d56-119">Tipos</span><span class="sxs-lookup"><span data-stu-id="a7d56-119">Types</span></span>](types.md)
- [<span data-ttu-id="a7d56-120">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="a7d56-120">Value Types</span></span>](value-types.md)
