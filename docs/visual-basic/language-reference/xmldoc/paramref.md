---
title: <paramref>
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 78227a17584271f91283198e95f5aa389b3ef14b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352276"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="278fc-101">\<paramref > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="278fc-101">\<paramref> (Visual Basic)</span></span>
<span data-ttu-id="278fc-102">Formata uma palavra como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="278fc-102">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="278fc-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="278fc-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="278fc-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="278fc-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="278fc-105">O nome do parâmetro ao qual você deseja se referir.</span><span class="sxs-lookup"><span data-stu-id="278fc-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="278fc-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="278fc-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="278fc-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="278fc-107">Remarks</span></span>  
 <span data-ttu-id="278fc-108">A marca `<paramref>` fornece uma maneira de indicar que uma palavra é um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="278fc-108">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="278fc-109">O arquivo XML pode ser processado para formatar esse parâmetro de uma maneira distinta.</span><span class="sxs-lookup"><span data-stu-id="278fc-109">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="278fc-110">Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="278fc-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="278fc-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="278fc-111">Example</span></span>  
 <span data-ttu-id="278fc-112">Este exemplo usa a marca `<paramref>` para fazer referência ao parâmetro `id`.</span><span class="sxs-lookup"><span data-stu-id="278fc-112">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="278fc-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="278fc-113">See also</span></span>

- [<span data-ttu-id="278fc-114">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="278fc-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
