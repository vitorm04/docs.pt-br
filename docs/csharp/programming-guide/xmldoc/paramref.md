---
title: <paramref> – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: e6d6c62c97179d74bdb6bdd88eeb1ee129226fed
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201398"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="93396-102">\<paramref> (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="93396-102">\<paramref> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="93396-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="93396-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93396-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="93396-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="93396-105">O nome do parâmetro ao qual você deseja se referir.</span><span class="sxs-lookup"><span data-stu-id="93396-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="93396-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="93396-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93396-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="93396-107">Remarks</span></span>  
 <span data-ttu-id="93396-108">A marca \<paramref> fornece uma maneira de indicar que uma palavra nos comentários do código, por exemplo, em um blogo \<summary> ou \<remarks> refere-se a um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="93396-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="93396-109">O arquivo XML pode ser processado para formatar essa palavra de alguma forma distinta, como com uma fonte em negrito ou itálico.</span><span class="sxs-lookup"><span data-stu-id="93396-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="93396-110">Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="93396-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93396-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="93396-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]  
  
## <a name="see-also"></a><span data-ttu-id="93396-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93396-112">See also</span></span>

- [<span data-ttu-id="93396-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="93396-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="93396-114">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="93396-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
