---
title: '#pragma – Referência de C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 65ca38ff6993117b6ed9f716d4ac93ba2d4a9ddf
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605661"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="91587-102">#pragma (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="91587-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="91587-103">O `#pragma` fornece ao compilador instruções especiais para a compilação do arquivo no qual ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="91587-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="91587-104">O compilador deve dar suporte às instruções.</span><span class="sxs-lookup"><span data-stu-id="91587-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="91587-105">Em outras palavras, não é possível usar `#pragma` para criar instruções personalizadas de pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="91587-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="91587-106">O compilador Microsoft C# dá suporte a estas duas `#pragma` instruções:</span><span class="sxs-lookup"><span data-stu-id="91587-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="91587-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="91587-107">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="91587-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="91587-108">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="91587-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91587-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="91587-110">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="91587-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="91587-111">O nome de um pragma reconhecido.</span><span class="sxs-lookup"><span data-stu-id="91587-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="91587-112">Argumentos específicos do pragma.</span><span class="sxs-lookup"><span data-stu-id="91587-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91587-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91587-113">See also</span></span>

- [<span data-ttu-id="91587-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="91587-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="91587-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="91587-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="91587-116">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="91587-116">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="91587-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="91587-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="91587-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="91587-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)
