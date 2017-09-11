---
title: "#<a name=\"pragma-warning-c-reference\"></a>pragma warning (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma warning'
dev_langs:
- CSharp
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 75c11acfd096d36c96ceb9e9c5c0d16e47e58fa1
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="4e49e-102">#pragma warning (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4e49e-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="4e49e-103">O `#pragma warning` pode habilitar ou desabilitar determinados avisos.</span><span class="sxs-lookup"><span data-stu-id="4e49e-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e49e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4e49e-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4e49e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4e49e-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="4e49e-106">Uma lista de números de aviso separada por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="4e49e-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="4e49e-107">O prefixo "CS" é opcional.</span><span class="sxs-lookup"><span data-stu-id="4e49e-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="4e49e-108">Quando não houver números de aviso especificados, o `disable` desabilita todos os avisos e o `restore` habilita todos os avisos.</span><span class="sxs-lookup"><span data-stu-id="4e49e-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e49e-109">Para localizar números de aviso no Visual Studio, compile o projeto e, em seguida, procure os números de aviso na janela de **Saída**.</span><span class="sxs-lookup"><span data-stu-id="4e49e-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e49e-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e49e-110">Example</span></span>  
  
```csharp
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, CS3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore CS3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e49e-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e49e-111">See Also</span></span>  
 <span data-ttu-id="4e49e-112">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="4e49e-112">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="4e49e-113">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4e49e-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4e49e-114">[Diretivas de pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md) </span><span class="sxs-lookup"><span data-stu-id="4e49e-114">[C# Preprocessor Directives](../../../csharp/language-reference/preprocessor-directives/index.md) </span></span>  
 [<span data-ttu-id="4e49e-115">Erros do Compilador do C#</span><span class="sxs-lookup"><span data-stu-id="4e49e-115">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)

