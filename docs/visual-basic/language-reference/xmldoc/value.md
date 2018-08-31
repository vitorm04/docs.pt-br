---
title: '&lt;valor&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: ef14836c438cf6a1de300270d9882c1e53e716ee
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258037"
---
# <a name="ltvaluegt-visual-basic"></a><span data-ttu-id="a8c4a-102">&lt;valor&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8c4a-102">&lt;value&gt; (Visual Basic)</span></span>
<span data-ttu-id="a8c4a-103">Especifica a descrição de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="a8c4a-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8c4a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8c4a-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a8c4a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a8c4a-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="a8c4a-106">Uma descrição da propriedade.</span><span class="sxs-lookup"><span data-stu-id="a8c4a-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8c4a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8c4a-107">Remarks</span></span>  
 <span data-ttu-id="a8c4a-108">Use o `<value>` marca para descrever uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="a8c4a-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="a8c4a-109">Observe que quando você adiciona uma propriedade usando o Assistente de código no ambiente de desenvolvimento do Visual Studio, ele adicionará um [ \<resumo >](../../../visual-basic/language-reference/xmldoc/summary.md) marca para a nova propriedade.</span><span class="sxs-lookup"><span data-stu-id="a8c4a-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="a8c4a-110">Você deve adicionar manualmente um `<value>` marca para descrever o valor que representa a propriedade.</span><span class="sxs-lookup"><span data-stu-id="a8c4a-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="a8c4a-111">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="a8c4a-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8c4a-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8c4a-112">Example</span></span>  
 <span data-ttu-id="a8c4a-113">Este exemplo usa o `<value>` marca para descrever qual valor o `Counter` isenções de propriedade.</span><span class="sxs-lookup"><span data-stu-id="a8c4a-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a8c4a-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8c4a-114">See Also</span></span>  
 [<span data-ttu-id="a8c4a-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="a8c4a-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
