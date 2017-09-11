---
title: "Parâmetros de método (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
caps.latest.revision: 8
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4ba57e1a9e904befe11ff41796c987bd8f93b081
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="f7930-102">Parâmetros de método (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="f7930-102">Method Parameters (C# Reference)</span></span>
<span data-ttu-id="f7930-103">Se um parâmetro for declarado para um método sem [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md), o parâmetro pode ter um valor associado a ele.</span><span class="sxs-lookup"><span data-stu-id="f7930-103">If a parameter is declared for a method without [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md), the parameter can have a value associated with it.</span></span> <span data-ttu-id="f7930-104">Esse valor pode ser alterado no método, mas o valor alterado não será mantido quando o controle passá-lo de volta para o procedimento de chamada.</span><span class="sxs-lookup"><span data-stu-id="f7930-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="f7930-105">É possível alterar esse comportamento usando uma palavra-chave de parâmetro de método.</span><span class="sxs-lookup"><span data-stu-id="f7930-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="f7930-106">Esta seção descreve as palavras-chave que podem ser usadas ao declarar parâmetros de método:</span><span class="sxs-lookup"><span data-stu-id="f7930-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   [<span data-ttu-id="f7930-107">params</span><span class="sxs-lookup"><span data-stu-id="f7930-107">params</span></span>](../../../csharp/language-reference/keywords/params.md)  
  
-   [<span data-ttu-id="f7930-108">ref</span><span class="sxs-lookup"><span data-stu-id="f7930-108">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
  
-   [<span data-ttu-id="f7930-109">out</span><span class="sxs-lookup"><span data-stu-id="f7930-109">out</span></span>](../../../csharp/language-reference/keywords/out.md)  
  
## <a name="see-also"></a><span data-ttu-id="f7930-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7930-110">See Also</span></span>  
 <span data-ttu-id="f7930-111">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f7930-111">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f7930-112">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f7930-112">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="f7930-113">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="f7930-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)

