---
title: "&lt;paramref&gt; (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fff532c02538f121ebe399e1780d8c19d9d6633a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltparamrefgt-c-programming-guide"></a><span data-ttu-id="11004-102">&lt;paramref&gt; (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="11004-102">&lt;paramref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="11004-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11004-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11004-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11004-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="11004-105">O nome do parâmetro ao qual você deseja se referir.</span><span class="sxs-lookup"><span data-stu-id="11004-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="11004-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="11004-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11004-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="11004-107">Remarks</span></span>  
 <span data-ttu-id="11004-108">A marca \<paramref> fornece uma maneira de indicar que uma palavra nos comentários do código, por exemplo, em um blogo \<summary> ou \<remarks> refere-se a um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="11004-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="11004-109">O arquivo XML pode ser processado para formatar essa palavra de alguma forma distinta, como com uma fonte em negrito ou itálico.</span><span class="sxs-lookup"><span data-stu-id="11004-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="11004-110">Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="11004-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11004-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="11004-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="11004-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11004-112">See Also</span></span>  
 [<span data-ttu-id="11004-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="11004-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="11004-114">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="11004-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
