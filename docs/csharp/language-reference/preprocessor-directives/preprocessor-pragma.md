---
description: '#pragma – Referência de C#'
title: '#pragma – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 2788c2589bee149676c5cb2b4212ec7a060a47af
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168511"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="3819a-103">#pragma (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="3819a-103">#pragma (C# Reference)</span></span>

<span data-ttu-id="3819a-104">O `#pragma` fornece ao compilador instruções especiais para a compilação do arquivo no qual ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="3819a-104">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="3819a-105">O compilador deve dar suporte às instruções.</span><span class="sxs-lookup"><span data-stu-id="3819a-105">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="3819a-106">Em outras palavras, não é possível usar `#pragma` para criar instruções personalizadas de pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="3819a-106">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="3819a-107">O compilador Microsoft C# dá suporte a estas duas `#pragma` instruções:</span><span class="sxs-lookup"><span data-stu-id="3819a-107">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="3819a-108">aviso de #pragma</span><span class="sxs-lookup"><span data-stu-id="3819a-108">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="3819a-109">soma de verificação de #pragma</span><span class="sxs-lookup"><span data-stu-id="3819a-109">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="3819a-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3819a-110">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="3819a-111">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3819a-111">Parameters</span></span>  

 `pragma-name`  
 <span data-ttu-id="3819a-112">O nome de um pragma reconhecido.</span><span class="sxs-lookup"><span data-stu-id="3819a-112">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="3819a-113">Argumentos específicos do pragma.</span><span class="sxs-lookup"><span data-stu-id="3819a-113">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3819a-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="3819a-114">See also</span></span>

- [<span data-ttu-id="3819a-115">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="3819a-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3819a-116">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="3819a-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3819a-117">Diretivas de pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="3819a-117">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="3819a-118">aviso de #pragma</span><span class="sxs-lookup"><span data-stu-id="3819a-118">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="3819a-119">soma de verificação de #pragma</span><span class="sxs-lookup"><span data-stu-id="3819a-119">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)
