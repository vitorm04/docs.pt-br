---
description: '#pragma – Referência de C#'
title: '#pragma – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 97d7a786c83a8be21f7fd38873061dba0f9278ae
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137949"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="8fcd8-103">#pragma (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="8fcd8-103">#pragma (C# Reference)</span></span>
<span data-ttu-id="8fcd8-104">O `#pragma` fornece ao compilador instruções especiais para a compilação do arquivo no qual ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="8fcd8-104">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="8fcd8-105">O compilador deve dar suporte às instruções.</span><span class="sxs-lookup"><span data-stu-id="8fcd8-105">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="8fcd8-106">Em outras palavras, não é possível usar `#pragma` para criar instruções personalizadas de pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="8fcd8-106">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="8fcd8-107">O compilador Microsoft C# dá suporte a estas duas `#pragma` instruções:</span><span class="sxs-lookup"><span data-stu-id="8fcd8-107">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="8fcd8-108">aviso de #pragma</span><span class="sxs-lookup"><span data-stu-id="8fcd8-108">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="8fcd8-109">soma de verificação de #pragma</span><span class="sxs-lookup"><span data-stu-id="8fcd8-109">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="8fcd8-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8fcd8-110">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fcd8-111">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8fcd8-111">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="8fcd8-112">O nome de um pragma reconhecido.</span><span class="sxs-lookup"><span data-stu-id="8fcd8-112">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="8fcd8-113">Argumentos específicos do pragma.</span><span class="sxs-lookup"><span data-stu-id="8fcd8-113">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fcd8-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="8fcd8-114">See also</span></span>

- [<span data-ttu-id="8fcd8-115">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="8fcd8-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8fcd8-116">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="8fcd8-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8fcd8-117">Diretivas de pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="8fcd8-117">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="8fcd8-118">aviso de #pragma</span><span class="sxs-lookup"><span data-stu-id="8fcd8-118">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="8fcd8-119">soma de verificação de #pragma</span><span class="sxs-lookup"><span data-stu-id="8fcd8-119">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)
