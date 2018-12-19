---
title: '#pragma – Referência de C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 65867bc441711193f93142d1c65122b6bc60c25d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241821"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="9a5d2-102">#pragma (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="9a5d2-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="9a5d2-103">O `#pragma` fornece ao compilador instruções especiais para a compilação do arquivo no qual ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="9a5d2-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="9a5d2-104">O compilador deve dar suporte às instruções.</span><span class="sxs-lookup"><span data-stu-id="9a5d2-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="9a5d2-105">Em outras palavras, não é possível usar `#pragma` para criar instruções personalizadas de pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="9a5d2-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="9a5d2-106">O compilador Microsoft C# dá suporte a estas duas `#pragma` instruções:</span><span class="sxs-lookup"><span data-stu-id="9a5d2-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="9a5d2-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="9a5d2-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="9a5d2-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="9a5d2-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="9a5d2-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a5d2-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a5d2-110">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9a5d2-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="9a5d2-111">O nome de um pragma reconhecido.</span><span class="sxs-lookup"><span data-stu-id="9a5d2-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="9a5d2-112">Argumentos específicos do pragma.</span><span class="sxs-lookup"><span data-stu-id="9a5d2-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a5d2-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a5d2-113">See Also</span></span>

- [<span data-ttu-id="9a5d2-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="9a5d2-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="9a5d2-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="9a5d2-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9a5d2-116">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="9a5d2-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
- [<span data-ttu-id="9a5d2-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="9a5d2-117">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
- [<span data-ttu-id="9a5d2-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="9a5d2-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)
