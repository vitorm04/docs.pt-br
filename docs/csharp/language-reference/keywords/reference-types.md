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
ms.openlocfilehash: b2d6cc94c11ca6305a75e9ee489af53ad957201e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76744523"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="03f11-102">Tipos de referência (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="03f11-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="03f11-103">Há dois tipos em C#: tipos de referência e valor.</span><span class="sxs-lookup"><span data-stu-id="03f11-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="03f11-104">Variáveis de tipos de referência armazenam referências em seus dados (objetos) enquanto que variáveis de tipos de valor contém diretamente seus dados.</span><span class="sxs-lookup"><span data-stu-id="03f11-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="03f11-105">Com tipos de referência, duas variáveis podem fazer referência ao mesmo objeto; portanto, operações em uma variável podem afetar o objeto referenciado pela outra variável.</span><span class="sxs-lookup"><span data-stu-id="03f11-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="03f11-106">Com tipos de valor, cada variável tem sua própria cópia dos dados e as operações em uma variável não podem afetar a outra (exceto no caso das variáveis de parâmetros in, ref e out. Confira o modificador de parâmetro [in](in-parameter-modifier.md), [ref](ref.md) e [out](out-parameter-modifier.md)).</span><span class="sxs-lookup"><span data-stu-id="03f11-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="03f11-107">As seguintes palavras-chaves são usadas para declarar tipos de referência:</span><span class="sxs-lookup"><span data-stu-id="03f11-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="03f11-108">class</span><span class="sxs-lookup"><span data-stu-id="03f11-108">class</span></span>](class.md)

- [<span data-ttu-id="03f11-109">Interface</span><span class="sxs-lookup"><span data-stu-id="03f11-109">interface</span></span>](interface.md)

- [<span data-ttu-id="03f11-110">Delegado</span><span class="sxs-lookup"><span data-stu-id="03f11-110">delegate</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="03f11-111">O C# também oferece os seguintes tipos de referência internos:</span><span class="sxs-lookup"><span data-stu-id="03f11-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="03f11-112">dinâmico</span><span class="sxs-lookup"><span data-stu-id="03f11-112">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="03f11-113">Objeto</span><span class="sxs-lookup"><span data-stu-id="03f11-113">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="03f11-114">String</span><span class="sxs-lookup"><span data-stu-id="03f11-114">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="03f11-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="03f11-115">See also</span></span>

- [<span data-ttu-id="03f11-116">C# Referência</span><span class="sxs-lookup"><span data-stu-id="03f11-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="03f11-117">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="03f11-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="03f11-118">Tipos de Ponteiro</span><span class="sxs-lookup"><span data-stu-id="03f11-118">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="03f11-119">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="03f11-119">Value types</span></span>](../builtin-types/value-types.md)
