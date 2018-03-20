---
title: "Parâmetros de método (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b20d2d233350cfb9de55cbd07e722082ec311597
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="e534d-102">Parâmetros de método (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e534d-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="e534d-103">Os parâmetros declarados para um método sem [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) nem [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) são passados para o método chamado pelo valor.</span><span class="sxs-lookup"><span data-stu-id="e534d-103">Parameters declared for a method without [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="e534d-104">Esse valor pode ser alterado no método, mas o valor alterado não será mantido quando o controle passá-lo de volta para o procedimento de chamada.</span><span class="sxs-lookup"><span data-stu-id="e534d-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="e534d-105">É possível alterar esse comportamento usando uma palavra-chave de parâmetro de método.</span><span class="sxs-lookup"><span data-stu-id="e534d-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="e534d-106">Esta seção descreve as palavras-chave que podem ser usadas ao declarar parâmetros de método:</span><span class="sxs-lookup"><span data-stu-id="e534d-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   [<span data-ttu-id="e534d-107">params</span><span class="sxs-lookup"><span data-stu-id="e534d-107">params</span></span>](../../../csharp/language-reference/keywords/params.md)  
  
-   [<span data-ttu-id="e534d-108">in</span><span class="sxs-lookup"><span data-stu-id="e534d-108">in</span></span>](../../../csharp/language-reference/keywords/in-parameter-modifier.md)  
  
-   [<span data-ttu-id="e534d-109">ref</span><span class="sxs-lookup"><span data-stu-id="e534d-109">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
  
-   [<span data-ttu-id="e534d-110">out</span><span class="sxs-lookup"><span data-stu-id="e534d-110">out</span></span>](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
  
## <a name="see-also"></a><span data-ttu-id="e534d-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e534d-111">See Also</span></span>  
 [<span data-ttu-id="e534d-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e534d-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e534d-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e534d-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e534d-114">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="e534d-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
