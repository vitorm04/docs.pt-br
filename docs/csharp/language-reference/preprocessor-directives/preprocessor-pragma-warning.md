---
description: '##pragma warning – Referência de C#'
title: '##pragma warning – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 3085c21db386ca215d48bbe8ade83cd26732242c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137962"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="4f532-103">#pragma warning (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4f532-103">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="4f532-104">O `#pragma warning` pode habilitar ou desabilitar determinados avisos.</span><span class="sxs-lookup"><span data-stu-id="4f532-104">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f532-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f532-105">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f532-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4f532-106">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="4f532-107">Uma lista de números de aviso separada por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="4f532-107">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="4f532-108">O prefixo "CS" é opcional.</span><span class="sxs-lookup"><span data-stu-id="4f532-108">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="4f532-109">Quando não houver números de aviso especificados, o `disable` desabilita todos os avisos e o `restore` habilita todos os avisos.</span><span class="sxs-lookup"><span data-stu-id="4f532-109">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f532-110">Para localizar números de aviso no Visual Studio, compile o projeto e, em seguida, procure os números de aviso na janela de **Saída**.</span><span class="sxs-lookup"><span data-stu-id="4f532-110">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f532-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f532-111">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4f532-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="4f532-112">See also</span></span>

- [<span data-ttu-id="4f532-113">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="4f532-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4f532-114">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="4f532-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4f532-115">Diretivas de pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="4f532-115">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="4f532-116">Erros do compilador C#</span><span class="sxs-lookup"><span data-stu-id="4f532-116">C# Compiler Errors</span></span>](../compiler-messages/index.md)
