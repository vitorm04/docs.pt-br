---
title: '#pragma warning (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 079045f4eb52f03afa8733620029396d80cb75fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273651"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="bdd7c-102">#pragma warning (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="bdd7c-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="bdd7c-103">O `#pragma warning` pode habilitar ou desabilitar determinados avisos.</span><span class="sxs-lookup"><span data-stu-id="bdd7c-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdd7c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bdd7c-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bdd7c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bdd7c-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="bdd7c-106">Uma lista de números de aviso separada por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="bdd7c-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="bdd7c-107">O prefixo "CS" é opcional.</span><span class="sxs-lookup"><span data-stu-id="bdd7c-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="bdd7c-108">Quando não houver números de aviso especificados, o `disable` desabilita todos os avisos e o `restore` habilita todos os avisos.</span><span class="sxs-lookup"><span data-stu-id="bdd7c-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdd7c-109">Para localizar números de aviso no Visual Studio, compile o projeto e, em seguida, procure os números de aviso na janela de **Saída**.</span><span class="sxs-lookup"><span data-stu-id="bdd7c-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdd7c-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bdd7c-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bdd7c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bdd7c-111">See Also</span></span>  
 [<span data-ttu-id="bdd7c-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="bdd7c-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bdd7c-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="bdd7c-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bdd7c-114">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="bdd7c-114">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="bdd7c-115">Erros do Compilador do C#</span><span class="sxs-lookup"><span data-stu-id="bdd7c-115">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
