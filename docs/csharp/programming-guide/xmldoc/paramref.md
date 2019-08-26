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
ms.openlocfilehash: e442b6829859ebc4dce6a0f5b6cd6cb777ab1400
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587913"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="fca12-102">\<paramref> (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="fca12-102">\<paramref> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="fca12-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fca12-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="fca12-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fca12-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="fca12-105">O nome do parâmetro ao qual você deseja se referir.</span><span class="sxs-lookup"><span data-stu-id="fca12-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="fca12-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="fca12-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fca12-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="fca12-107">Remarks</span></span>  
 <span data-ttu-id="fca12-108">A marca \<paramref> fornece uma maneira de indicar que uma palavra nos comentários do código, por exemplo, em um blogo \<summary> ou \<remarks> refere-se a um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fca12-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="fca12-109">O arquivo XML pode ser processado para formatar essa palavra de alguma forma distinta, como com uma fonte em negrito ou itálico.</span><span class="sxs-lookup"><span data-stu-id="fca12-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="fca12-110">Compile com [/doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="fca12-110">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fca12-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fca12-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]  
  
## <a name="see-also"></a><span data-ttu-id="fca12-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fca12-112">See also</span></span>

- [<span data-ttu-id="fca12-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="fca12-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fca12-114">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="fca12-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
