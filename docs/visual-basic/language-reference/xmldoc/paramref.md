---
title: '&lt;paramref&gt; (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: a5ecb3a6ece40e04cb3a01044750bf28bc7d2cb2
ms.contentlocale: pt-br
ms.lasthandoff: 06/01/2017

---
# <a name="ltparamrefgt-visual-basic"></a><span data-ttu-id="5908a-102">&lt;paramref&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5908a-102">&lt;paramref&gt; (Visual Basic)</span></span>
<span data-ttu-id="5908a-103">Formata uma palavra como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5908a-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5908a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5908a-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5908a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5908a-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="5908a-106">O nome do parâmetro para referir-se.</span><span class="sxs-lookup"><span data-stu-id="5908a-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="5908a-107">Coloque o nome entre aspas duplas ("").</span><span class="sxs-lookup"><span data-stu-id="5908a-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5908a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="5908a-108">Remarks</span></span>  
 <span data-ttu-id="5908a-109">O `<paramref>` marca fornece uma maneira para indicar que uma palavra é um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5908a-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="5908a-110">O arquivo XML pode ser processado para formatar este parâmetro em alguma forma distinta.</span><span class="sxs-lookup"><span data-stu-id="5908a-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="5908a-111">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="5908a-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5908a-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5908a-112">Example</span></span>  
 <span data-ttu-id="5908a-113">Este exemplo usa o `<paramref>` marca para referir-se a `id` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5908a-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 <span data-ttu-id="5908a-114">[!code-vb[VbVbcnXmlDocComments n º&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5908a-114">[!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5908a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5908a-115">See Also</span></span>  
 [<span data-ttu-id="5908a-116">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="5908a-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
