---
title: '##pragma warning – Referência de C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 0145df533572ff9d5004a653bb232a7ff60af5f1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495098"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="7ec0f-102">#pragma warning (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7ec0f-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="7ec0f-103">O `#pragma warning` pode habilitar ou desabilitar determinados avisos.</span><span class="sxs-lookup"><span data-stu-id="7ec0f-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ec0f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ec0f-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ec0f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7ec0f-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="7ec0f-106">Uma lista de números de aviso separada por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="7ec0f-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="7ec0f-107">O prefixo "CS" é opcional.</span><span class="sxs-lookup"><span data-stu-id="7ec0f-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="7ec0f-108">Quando não houver números de aviso especificados, o `disable` desabilita todos os avisos e o `restore` habilita todos os avisos.</span><span class="sxs-lookup"><span data-stu-id="7ec0f-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ec0f-109">Para localizar números de aviso no Visual Studio, compile o projeto e, em seguida, procure os números de aviso na janela de **Saída**.</span><span class="sxs-lookup"><span data-stu-id="7ec0f-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ec0f-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7ec0f-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7ec0f-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ec0f-111">See also</span></span>

- [<span data-ttu-id="7ec0f-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="7ec0f-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="7ec0f-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7ec0f-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="7ec0f-114">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="7ec0f-114">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
- [<span data-ttu-id="7ec0f-115">Erros do Compilador do C#</span><span class="sxs-lookup"><span data-stu-id="7ec0f-115">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
