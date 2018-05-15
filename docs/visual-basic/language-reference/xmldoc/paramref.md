---
title: '&lt;paramref&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 763e311dfb46ceeed358c3b3bebd6212d3e2489c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ltparamrefgt-visual-basic"></a><span data-ttu-id="a01af-102">&lt;paramref&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a01af-102">&lt;paramref&gt; (Visual Basic)</span></span>
<span data-ttu-id="a01af-103">Formata uma palavra como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a01af-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a01af-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a01af-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a01af-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a01af-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="a01af-106">O nome do parâmetro ao qual você deseja se referir.</span><span class="sxs-lookup"><span data-stu-id="a01af-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="a01af-107">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="a01af-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a01af-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a01af-108">Remarks</span></span>  
 <span data-ttu-id="a01af-109">O `<paramref>` marca fornece uma maneira para indicar que uma palavra é um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a01af-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="a01af-110">O arquivo XML pode ser processado para formatar esse parâmetro em alguma forma distinta.</span><span class="sxs-lookup"><span data-stu-id="a01af-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="a01af-111">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="a01af-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a01af-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a01af-112">Example</span></span>  
 <span data-ttu-id="a01af-113">Este exemplo usa o `<paramref>` marca para referir-se a `id` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a01af-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a01af-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a01af-114">See Also</span></span>  
 [<span data-ttu-id="a01af-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="a01af-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
