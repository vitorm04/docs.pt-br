---
title: "#<a name=\"pragma-c-reference\"></a>pragma (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma'
dev_langs:
- CSharp
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e03fc387b105c1dee3b7fed93263ad8ef22d5934
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="pragma-c-reference"></a><span data-ttu-id="f97db-102">#pragma (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="f97db-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="f97db-103">O `#pragma` fornece ao compilador instruções especiais para a compilação do arquivo no qual ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="f97db-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="f97db-104">O compilador deve dar suporte às instruções.</span><span class="sxs-lookup"><span data-stu-id="f97db-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="f97db-105">Em outras palavras, não é possível usar `#pragma` para criar instruções personalizadas de pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="f97db-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="f97db-106">O compilador Microsoft C# dá suporte a estas duas `#pragma` instruções:</span><span class="sxs-lookup"><span data-stu-id="f97db-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="f97db-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="f97db-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="f97db-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="f97db-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="f97db-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f97db-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f97db-110">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f97db-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="f97db-111">O nome de um pragma reconhecido.</span><span class="sxs-lookup"><span data-stu-id="f97db-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="f97db-112">Argumentos específicos do pragma.</span><span class="sxs-lookup"><span data-stu-id="f97db-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f97db-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f97db-113">See Also</span></span>  
 <span data-ttu-id="f97db-114">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f97db-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f97db-115">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f97db-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f97db-116">[Diretivas de pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md) </span><span class="sxs-lookup"><span data-stu-id="f97db-116">[C# Preprocessor Directives](../../../csharp/language-reference/preprocessor-directives/index.md) </span></span>  
 <span data-ttu-id="f97db-117">[Aviso #pragma](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) </span><span class="sxs-lookup"><span data-stu-id="f97db-117">[#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) </span></span>  
 [<span data-ttu-id="f97db-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="f97db-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

