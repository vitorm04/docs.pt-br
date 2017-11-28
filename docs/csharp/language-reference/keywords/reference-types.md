---
title: "Tipos de referência (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4f87363246deccf282b499aa2afee2a14d41593
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="8a5f3-102">Tipos de referência (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="8a5f3-102">Reference Types (C# Reference)</span></span>
<span data-ttu-id="8a5f3-103">Há dois tipos em C#: tipos de referência e valor.</span><span class="sxs-lookup"><span data-stu-id="8a5f3-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="8a5f3-104">Variáveis de tipos de referência armazenam referências em seus dados (objetos) enquanto que variáveis de tipos de valor contém diretamente seus dados.</span><span class="sxs-lookup"><span data-stu-id="8a5f3-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="8a5f3-105">Com tipos de referência, duas variáveis podem fazer referência ao mesmo objeto; portanto, operações em uma variável podem afetar o objeto referenciado pela outra variável.</span><span class="sxs-lookup"><span data-stu-id="8a5f3-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="8a5f3-106">Com tipos de valor, cada variável tem sua própria cópia dos dados e não é possível que as operações em uma variável afetem a outra (exceto no caso de variáveis de parâmetros ref e out, consulte [ref](../../../csharp/language-reference/keywords/ref.md) e [modificador de parâmetro out](../../../csharp/language-reference/keywords/out-parameter-modifier.md)).</span><span class="sxs-lookup"><span data-stu-id="8a5f3-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of ref and out parameter variables, see [ref](../../../csharp/language-reference/keywords/ref.md) and [out parameter modifier](../../../csharp/language-reference/keywords/out-parameter-modifier.md)).</span></span>  
  
 <span data-ttu-id="8a5f3-107">As seguintes palavras-chaves são usadas para declarar tipos de referência:</span><span class="sxs-lookup"><span data-stu-id="8a5f3-107">The following keywords are used to declare reference types:</span></span>  
  
-   [<span data-ttu-id="8a5f3-108">class</span><span class="sxs-lookup"><span data-stu-id="8a5f3-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="8a5f3-109">interface</span><span class="sxs-lookup"><span data-stu-id="8a5f3-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="8a5f3-110">delegate</span><span class="sxs-lookup"><span data-stu-id="8a5f3-110">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="8a5f3-111">O C# também oferece os seguintes tipos de referência internos:</span><span class="sxs-lookup"><span data-stu-id="8a5f3-111">C# also provides the following built-in reference types:</span></span>  
  
-   [<span data-ttu-id="8a5f3-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="8a5f3-112">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
  
-   [<span data-ttu-id="8a5f3-113">object</span><span class="sxs-lookup"><span data-stu-id="8a5f3-113">object</span></span>](../../../csharp/language-reference/keywords/object.md)  
  
-   [<span data-ttu-id="8a5f3-114">string</span><span class="sxs-lookup"><span data-stu-id="8a5f3-114">string</span></span>](../../../csharp/language-reference/keywords/string.md)  
  
## <a name="see-also"></a><span data-ttu-id="8a5f3-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a5f3-115">See Also</span></span>  
 [<span data-ttu-id="8a5f3-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="8a5f3-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8a5f3-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="8a5f3-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8a5f3-118">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="8a5f3-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="8a5f3-119">Tipos</span><span class="sxs-lookup"><span data-stu-id="8a5f3-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="8a5f3-120">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="8a5f3-120">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
