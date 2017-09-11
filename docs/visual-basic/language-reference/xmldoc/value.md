---
title: '&lt;valor&gt; (Visual Basic) | Documentos do Microsoft'
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
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
caps.latest.revision: 10
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
ms.openlocfilehash: 630da0008f8368f08d6702a60cb64005fb2cf164
ms.contentlocale: pt-br
ms.lasthandoff: 06/01/2017

---
# <a name="ltvaluegt-visual-basic"></a><span data-ttu-id="08dcb-102">&lt;valor&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08dcb-102">&lt;value&gt; (Visual Basic)</span></span>
<span data-ttu-id="08dcb-103">Especifica a descrição de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="08dcb-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08dcb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08dcb-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08dcb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="08dcb-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="08dcb-106">Uma descrição da propriedade.</span><span class="sxs-lookup"><span data-stu-id="08dcb-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08dcb-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="08dcb-107">Remarks</span></span>  
 <span data-ttu-id="08dcb-108">Use o `<value>` marca para descrever uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="08dcb-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="08dcb-109">Observe que quando você adiciona uma propriedade usando o Assistente de código no ambiente de desenvolvimento do Visual Studio, ele adicionará um [ \<resumo >](../../../visual-basic/language-reference/xmldoc/summary.md) marca para a nova propriedade.</span><span class="sxs-lookup"><span data-stu-id="08dcb-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="08dcb-110">Você deve adicionar manualmente um `<value>` marca para descrever o valor que representa a propriedade.</span><span class="sxs-lookup"><span data-stu-id="08dcb-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="08dcb-111">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="08dcb-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08dcb-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="08dcb-112">Example</span></span>  
 <span data-ttu-id="08dcb-113">Este exemplo usa o `<value>` marca para descrever qual valor o `Counter` isenções de propriedade.</span><span class="sxs-lookup"><span data-stu-id="08dcb-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 <span data-ttu-id="08dcb-114">[!code-vb[VbVbcnXmlDocComments n º&1;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="08dcb-114">[!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08dcb-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08dcb-115">See Also</span></span>  
 [<span data-ttu-id="08dcb-116">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="08dcb-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
