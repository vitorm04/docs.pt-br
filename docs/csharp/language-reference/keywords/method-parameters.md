---
title: "Parâmetros de método (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 924e261cc876d2428e28ed0f490beb46b95f96e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="3e2ec-102">Parâmetros de método (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="3e2ec-102">Method Parameters (C# Reference)</span></span>
<span data-ttu-id="3e2ec-103">Se um parâmetro for declarado para um método sem [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md), o parâmetro pode ter um valor associado a ele.</span><span class="sxs-lookup"><span data-stu-id="3e2ec-103">If a parameter is declared for a method without [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md), the parameter can have a value associated with it.</span></span> <span data-ttu-id="3e2ec-104">Esse valor pode ser alterado no método, mas o valor alterado não será mantido quando o controle passá-lo de volta para o procedimento de chamada.</span><span class="sxs-lookup"><span data-stu-id="3e2ec-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="3e2ec-105">É possível alterar esse comportamento usando uma palavra-chave de parâmetro de método.</span><span class="sxs-lookup"><span data-stu-id="3e2ec-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="3e2ec-106">Esta seção descreve as palavras-chave que podem ser usadas ao declarar parâmetros de método:</span><span class="sxs-lookup"><span data-stu-id="3e2ec-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   [<span data-ttu-id="3e2ec-107">params</span><span class="sxs-lookup"><span data-stu-id="3e2ec-107">params</span></span>](../../../csharp/language-reference/keywords/params.md)  
  
-   [<span data-ttu-id="3e2ec-108">ref</span><span class="sxs-lookup"><span data-stu-id="3e2ec-108">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
  
-   [<span data-ttu-id="3e2ec-109">out</span><span class="sxs-lookup"><span data-stu-id="3e2ec-109">out</span></span>](../../../csharp/language-reference/keywords/out.md)  
  
## <a name="see-also"></a><span data-ttu-id="3e2ec-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e2ec-110">See Also</span></span>  
 [<span data-ttu-id="3e2ec-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="3e2ec-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3e2ec-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3e2ec-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3e2ec-113">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="3e2ec-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
