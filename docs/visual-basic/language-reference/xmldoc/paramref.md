---
title: <paramref> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 85171bd8deeb5f54c4560bb8b2339107bb8d8c68
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524711"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="1cabd-102">> de \<paramref (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1cabd-102">\<paramref> (Visual Basic)</span></span>
<span data-ttu-id="1cabd-103">Formata uma palavra como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1cabd-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cabd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1cabd-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cabd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1cabd-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="1cabd-106">O nome do parâmetro ao qual você deseja se referir.</span><span class="sxs-lookup"><span data-stu-id="1cabd-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="1cabd-107">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="1cabd-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cabd-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1cabd-108">Remarks</span></span>  
 <span data-ttu-id="1cabd-109">A marca `<paramref>` fornece uma maneira de indicar que uma palavra é um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1cabd-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="1cabd-110">O arquivo XML pode ser processado para formatar esse parâmetro de uma maneira distinta.</span><span class="sxs-lookup"><span data-stu-id="1cabd-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="1cabd-111">Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="1cabd-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cabd-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1cabd-112">Example</span></span>  
 <span data-ttu-id="1cabd-113">Este exemplo usa a marca `<paramref>` para fazer referência ao parâmetro `id`.</span><span class="sxs-lookup"><span data-stu-id="1cabd-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="1cabd-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cabd-114">See also</span></span>

- [<span data-ttu-id="1cabd-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="1cabd-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
