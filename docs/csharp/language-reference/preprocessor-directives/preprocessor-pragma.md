---
title: "#<a name=\"pragma-c-reference\"></a>pragma (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#pragma'
helpviewer_keywords: '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6f53bd0ed3f35f049b0a1cbb21c5b9a563f9fce9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-c-reference"></a><span data-ttu-id="c0e8c-102">#pragma (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="c0e8c-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="c0e8c-103">O `#pragma` fornece ao compilador instruções especiais para a compilação do arquivo no qual ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="c0e8c-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="c0e8c-104">O compilador deve dar suporte às instruções.</span><span class="sxs-lookup"><span data-stu-id="c0e8c-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="c0e8c-105">Em outras palavras, não é possível usar `#pragma` para criar instruções personalizadas de pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="c0e8c-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="c0e8c-106">O compilador Microsoft C# dá suporte a estas duas `#pragma` instruções:</span><span class="sxs-lookup"><span data-stu-id="c0e8c-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="c0e8c-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="c0e8c-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="c0e8c-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="c0e8c-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="c0e8c-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0e8c-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0e8c-110">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c0e8c-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="c0e8c-111">O nome de um pragma reconhecido.</span><span class="sxs-lookup"><span data-stu-id="c0e8c-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="c0e8c-112">Argumentos específicos do pragma.</span><span class="sxs-lookup"><span data-stu-id="c0e8c-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e8c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0e8c-113">See Also</span></span>  
 [<span data-ttu-id="c0e8c-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="c0e8c-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c0e8c-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c0e8c-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c0e8c-116">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="c0e8c-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="c0e8c-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="c0e8c-117">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
 [<span data-ttu-id="c0e8c-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="c0e8c-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)
