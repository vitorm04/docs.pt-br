---
description: '##pragma warning – Referência de C#'
title: '##pragma warning – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 5b67d384e37a5e509ce8ebcc5ddeb16a4437ea2b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168524"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="d0119-103">#pragma warning (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d0119-103">#pragma warning (C# Reference)</span></span>

<span data-ttu-id="d0119-104">O `#pragma warning` pode habilitar ou desabilitar determinados avisos.</span><span class="sxs-lookup"><span data-stu-id="d0119-104">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0119-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0119-105">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0119-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d0119-106">Parameters</span></span>  

 `warning-list`  
 <span data-ttu-id="d0119-107">Uma lista de números de aviso separada por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="d0119-107">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="d0119-108">O prefixo "CS" é opcional.</span><span class="sxs-lookup"><span data-stu-id="d0119-108">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="d0119-109">Quando não houver números de aviso especificados, o `disable` desabilita todos os avisos e o `restore` habilita todos os avisos.</span><span class="sxs-lookup"><span data-stu-id="d0119-109">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0119-110">Para localizar números de aviso no Visual Studio, compile o projeto e, em seguida, procure os números de aviso na janela de **Saída**.</span><span class="sxs-lookup"><span data-stu-id="d0119-110">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0119-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0119-111">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d0119-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="d0119-112">See also</span></span>

- [<span data-ttu-id="d0119-113">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="d0119-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d0119-114">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="d0119-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d0119-115">Diretivas de pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="d0119-115">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="d0119-116">Erros do compilador C#</span><span class="sxs-lookup"><span data-stu-id="d0119-116">C# Compiler Errors</span></span>](../compiler-messages/index.md)
