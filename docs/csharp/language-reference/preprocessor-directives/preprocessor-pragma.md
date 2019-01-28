---
title: '#pragma – Referência de C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 216adebae8a498ef2f4263f46f8ccd7a20d9202f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622371"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="cda21-102">#pragma (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="cda21-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="cda21-103">O `#pragma` fornece ao compilador instruções especiais para a compilação do arquivo no qual ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="cda21-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="cda21-104">O compilador deve dar suporte às instruções.</span><span class="sxs-lookup"><span data-stu-id="cda21-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="cda21-105">Em outras palavras, não é possível usar `#pragma` para criar instruções personalizadas de pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="cda21-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="cda21-106">O compilador Microsoft C# dá suporte a estas duas `#pragma` instruções:</span><span class="sxs-lookup"><span data-stu-id="cda21-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="cda21-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="cda21-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="cda21-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="cda21-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="cda21-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cda21-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cda21-110">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cda21-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="cda21-111">O nome de um pragma reconhecido.</span><span class="sxs-lookup"><span data-stu-id="cda21-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="cda21-112">Argumentos específicos do pragma.</span><span class="sxs-lookup"><span data-stu-id="cda21-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda21-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cda21-113">See also</span></span>

- [<span data-ttu-id="cda21-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="cda21-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="cda21-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="cda21-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="cda21-116">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="cda21-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
- [<span data-ttu-id="cda21-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="cda21-117">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)
- [<span data-ttu-id="cda21-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="cda21-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)
