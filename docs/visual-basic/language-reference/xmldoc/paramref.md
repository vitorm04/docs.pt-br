---
title: '&lt;paramref&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 153f5ddeeb7d09159049af4d466b0695f5cb6f23
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331353"
---
# <a name="ltparamrefgt-visual-basic"></a><span data-ttu-id="2cff6-102">&lt;paramref&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cff6-102">&lt;paramref&gt; (Visual Basic)</span></span>
<span data-ttu-id="2cff6-103">Formata uma palavra como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2cff6-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cff6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2cff6-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2cff6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2cff6-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="2cff6-106">O nome do parâmetro ao qual você deseja se referir.</span><span class="sxs-lookup"><span data-stu-id="2cff6-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="2cff6-107">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="2cff6-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cff6-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="2cff6-108">Remarks</span></span>  
 <span data-ttu-id="2cff6-109">O `<paramref>` marca oferece uma maneira para indicar que uma palavra é um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2cff6-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="2cff6-110">O arquivo XML pode ser processado para formatar esse parâmetro de alguma forma distinta.</span><span class="sxs-lookup"><span data-stu-id="2cff6-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="2cff6-111">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="2cff6-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cff6-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2cff6-112">Example</span></span>  
 <span data-ttu-id="2cff6-113">Este exemplo usa o `<paramref>` marca para referir-se a `id` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2cff6-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2cff6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2cff6-114">See Also</span></span>  
 [<span data-ttu-id="2cff6-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="2cff6-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
