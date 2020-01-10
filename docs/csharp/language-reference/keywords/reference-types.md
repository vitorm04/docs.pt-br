---
title: Tipos de referência – Referência em C#
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: 16e7cdc624979f9a35e287ea5274bd9398c83132
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715172"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="b7ed6-102">Tipos de referência (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="b7ed6-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="b7ed6-103">Há dois tipos em C#: tipos de referência e valor.</span><span class="sxs-lookup"><span data-stu-id="b7ed6-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="b7ed6-104">Variáveis de tipos de referência armazenam referências em seus dados (objetos) enquanto que variáveis de tipos de valor contém diretamente seus dados.</span><span class="sxs-lookup"><span data-stu-id="b7ed6-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="b7ed6-105">Com tipos de referência, duas variáveis podem fazer referência ao mesmo objeto; portanto, operações em uma variável podem afetar o objeto referenciado pela outra variável.</span><span class="sxs-lookup"><span data-stu-id="b7ed6-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="b7ed6-106">Com tipos de valor, cada variável tem sua própria cópia dos dados e as operações em uma variável não podem afetar a outra (exceto no caso das variáveis de parâmetros in, ref e out. Confira o modificador de parâmetro [in](in-parameter-modifier.md), [ref](ref.md) e [out](out-parameter-modifier.md)).</span><span class="sxs-lookup"><span data-stu-id="b7ed6-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="b7ed6-107">As seguintes palavras-chaves são usadas para declarar tipos de referência:</span><span class="sxs-lookup"><span data-stu-id="b7ed6-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="b7ed6-108">class</span><span class="sxs-lookup"><span data-stu-id="b7ed6-108">class</span></span>](class.md)

- [<span data-ttu-id="b7ed6-109">interface</span><span class="sxs-lookup"><span data-stu-id="b7ed6-109">interface</span></span>](interface.md)

- [<span data-ttu-id="b7ed6-110">delegate</span><span class="sxs-lookup"><span data-stu-id="b7ed6-110">delegate</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="b7ed6-111">O C# também oferece os seguintes tipos de referência internos:</span><span class="sxs-lookup"><span data-stu-id="b7ed6-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="b7ed6-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="b7ed6-112">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="b7ed6-113">object</span><span class="sxs-lookup"><span data-stu-id="b7ed6-113">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="b7ed6-114">string</span><span class="sxs-lookup"><span data-stu-id="b7ed6-114">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="b7ed6-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="b7ed6-115">See also</span></span>

- [<span data-ttu-id="b7ed6-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b7ed6-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b7ed6-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b7ed6-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b7ed6-118">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="b7ed6-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b7ed6-119">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="b7ed6-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="b7ed6-120">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="b7ed6-120">Value types</span></span>](value-types.md)
