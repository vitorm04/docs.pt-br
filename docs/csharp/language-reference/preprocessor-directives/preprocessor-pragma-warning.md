---
title: '##pragma warning – Referência de C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: dc221235e78a187f921815ed6e6c7750778014d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922270"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="a326d-102">#pragma warning (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a326d-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="a326d-103">O `#pragma warning` pode habilitar ou desabilitar determinados avisos.</span><span class="sxs-lookup"><span data-stu-id="a326d-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a326d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a326d-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="a326d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a326d-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="a326d-106">Uma lista de números de aviso separada por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="a326d-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="a326d-107">O prefixo "CS" é opcional.</span><span class="sxs-lookup"><span data-stu-id="a326d-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="a326d-108">Quando não houver números de aviso especificados, o `disable` desabilita todos os avisos e o `restore` habilita todos os avisos.</span><span class="sxs-lookup"><span data-stu-id="a326d-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a326d-109">Para localizar números de aviso no Visual Studio, compile o projeto e, em seguida, procure os números de aviso na janela de **Saída**.</span><span class="sxs-lookup"><span data-stu-id="a326d-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a326d-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a326d-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a326d-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a326d-111">See also</span></span>

- [<span data-ttu-id="a326d-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a326d-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a326d-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a326d-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a326d-114">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="a326d-114">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="a326d-115">Erros do Compilador do C#</span><span class="sxs-lookup"><span data-stu-id="a326d-115">C# Compiler Errors</span></span>](../compiler-messages/index.md)
