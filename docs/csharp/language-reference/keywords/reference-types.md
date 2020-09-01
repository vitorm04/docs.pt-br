---
description: Tipos de referência – Referência em C#
title: Tipos de referência – Referência em C#
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: 1a9df3c95d6f5052821be8db5ecf5a8ed99a8ba7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137052"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="fdd7e-103">Tipos de referência (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="fdd7e-103">Reference types (C# Reference)</span></span>

<span data-ttu-id="fdd7e-104">Há dois tipos em C#: tipos de referência e valor.</span><span class="sxs-lookup"><span data-stu-id="fdd7e-104">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="fdd7e-105">Variáveis de tipos de referência armazenam referências em seus dados (objetos) enquanto que variáveis de tipos de valor contém diretamente seus dados.</span><span class="sxs-lookup"><span data-stu-id="fdd7e-105">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="fdd7e-106">Com tipos de referência, duas variáveis podem fazer referência ao mesmo objeto; portanto, operações em uma variável podem afetar o objeto referenciado pela outra variável.</span><span class="sxs-lookup"><span data-stu-id="fdd7e-106">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="fdd7e-107">Com tipos de valor, cada variável tem sua própria cópia dos dados e as operações em uma variável não podem afetar a outra (exceto no caso das variáveis de parâmetros in, ref e out. Confira o modificador de parâmetro [in](in-parameter-modifier.md), [ref](ref.md) e [out](out-parameter-modifier.md)).</span><span class="sxs-lookup"><span data-stu-id="fdd7e-107">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="fdd7e-108">As seguintes palavras-chaves são usadas para declarar tipos de referência:</span><span class="sxs-lookup"><span data-stu-id="fdd7e-108">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="fdd7e-109">class</span><span class="sxs-lookup"><span data-stu-id="fdd7e-109">class</span></span>](class.md)

- [<span data-ttu-id="fdd7e-110">interface</span><span class="sxs-lookup"><span data-stu-id="fdd7e-110">interface</span></span>](interface.md)

- [<span data-ttu-id="fdd7e-111">delegate</span><span class="sxs-lookup"><span data-stu-id="fdd7e-111">delegate</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="fdd7e-112">O C# também oferece os seguintes tipos de referência internos:</span><span class="sxs-lookup"><span data-stu-id="fdd7e-112">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="fdd7e-113">dinâmico</span><span class="sxs-lookup"><span data-stu-id="fdd7e-113">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="fdd7e-114">object</span><span class="sxs-lookup"><span data-stu-id="fdd7e-114">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="fdd7e-115">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fdd7e-115">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="fdd7e-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="fdd7e-116">See also</span></span>

- [<span data-ttu-id="fdd7e-117">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="fdd7e-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fdd7e-118">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="fdd7e-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="fdd7e-119">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="fdd7e-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="fdd7e-120">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="fdd7e-120">Value types</span></span>](../builtin-types/value-types.md)
