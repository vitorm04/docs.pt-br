---
title: '#pragma – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 3bd62364aeae0f21715711324655ef7d00d88afc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712449"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="36672-102">#pragma (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="36672-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="36672-103">O `#pragma` fornece ao compilador instruções especiais para a compilação do arquivo no qual ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="36672-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="36672-104">O compilador deve dar suporte às instruções.</span><span class="sxs-lookup"><span data-stu-id="36672-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="36672-105">Em outras palavras, não é possível usar `#pragma` para criar instruções personalizadas de pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="36672-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="36672-106">O compilador Microsoft C# dá suporte a estas duas `#pragma` instruções:</span><span class="sxs-lookup"><span data-stu-id="36672-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="36672-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="36672-107">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="36672-108">#pragma soma de verificação</span><span class="sxs-lookup"><span data-stu-id="36672-108">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="36672-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36672-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="36672-110">parâmetros</span><span class="sxs-lookup"><span data-stu-id="36672-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="36672-111">O nome de um pragma reconhecido.</span><span class="sxs-lookup"><span data-stu-id="36672-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="36672-112">Argumentos específicos do pragma.</span><span class="sxs-lookup"><span data-stu-id="36672-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36672-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="36672-113">See also</span></span>

- [<span data-ttu-id="36672-114">C# Referência</span><span class="sxs-lookup"><span data-stu-id="36672-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="36672-115">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="36672-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="36672-116">C# Diretivas de pré-processador</span><span class="sxs-lookup"><span data-stu-id="36672-116">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="36672-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="36672-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="36672-118">#pragma soma de verificação</span><span class="sxs-lookup"><span data-stu-id="36672-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)
