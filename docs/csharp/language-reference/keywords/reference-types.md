---
title: Tipos de referência (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: cca9826c658581be38866410d5f966b1c7c35772
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267333"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="d29d9-102">Tipos de referência (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d29d9-102">Reference Types (C# Reference)</span></span>
<span data-ttu-id="d29d9-103">Há dois tipos em C#: tipos de referência e valor.</span><span class="sxs-lookup"><span data-stu-id="d29d9-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="d29d9-104">Variáveis de tipos de referência armazenam referências em seus dados (objetos) enquanto que variáveis de tipos de valor contém diretamente seus dados.</span><span class="sxs-lookup"><span data-stu-id="d29d9-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="d29d9-105">Com tipos de referência, duas variáveis podem fazer referência ao mesmo objeto; portanto, operações em uma variável podem afetar o objeto referenciado pela outra variável.</span><span class="sxs-lookup"><span data-stu-id="d29d9-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="d29d9-106">Com tipos de valor, cada variável tem sua própria cópia dos dados e as operações em uma variável não podem afetar a outra (exceto no caso das variáveis de parâmetros in, ref e out. Confira o modificador de parâmetro [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) e [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md)).</span><span class="sxs-lookup"><span data-stu-id="d29d9-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) and [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter modifier).</span></span>  
  
 <span data-ttu-id="d29d9-107">As seguintes palavras-chaves são usadas para declarar tipos de referência:</span><span class="sxs-lookup"><span data-stu-id="d29d9-107">The following keywords are used to declare reference types:</span></span>  
  
-   [<span data-ttu-id="d29d9-108">class</span><span class="sxs-lookup"><span data-stu-id="d29d9-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="d29d9-109">interface</span><span class="sxs-lookup"><span data-stu-id="d29d9-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="d29d9-110">delegate</span><span class="sxs-lookup"><span data-stu-id="d29d9-110">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="d29d9-111">O C# também oferece os seguintes tipos de referência internos:</span><span class="sxs-lookup"><span data-stu-id="d29d9-111">C# also provides the following built-in reference types:</span></span>  
  
-   [<span data-ttu-id="d29d9-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="d29d9-112">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
  
-   [<span data-ttu-id="d29d9-113">object</span><span class="sxs-lookup"><span data-stu-id="d29d9-113">object</span></span>](../../../csharp/language-reference/keywords/object.md)  
  
-   [<span data-ttu-id="d29d9-114">string</span><span class="sxs-lookup"><span data-stu-id="d29d9-114">string</span></span>](../../../csharp/language-reference/keywords/string.md)  
  
## <a name="see-also"></a><span data-ttu-id="d29d9-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d29d9-115">See Also</span></span>  
 [<span data-ttu-id="d29d9-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d29d9-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d29d9-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d29d9-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d29d9-118">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="d29d9-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d29d9-119">Tipos</span><span class="sxs-lookup"><span data-stu-id="d29d9-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="d29d9-120">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="d29d9-120">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
