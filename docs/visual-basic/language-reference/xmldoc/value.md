---
title: <value> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 5aab2307a1967ea660282c7b324eaddfe798a155
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857873"
---
# <a name="value-visual-basic"></a><span data-ttu-id="e62a0-102">\<valor > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e62a0-102">\<value> (Visual Basic)</span></span>
<span data-ttu-id="e62a0-103">Especifica a descrição de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="e62a0-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e62a0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e62a0-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e62a0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e62a0-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="e62a0-106">Uma descrição da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e62a0-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e62a0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e62a0-107">Remarks</span></span>  
 <span data-ttu-id="e62a0-108">Use o `<value>` marca para descrever uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="e62a0-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="e62a0-109">Observe que quando você adiciona uma propriedade usando o Assistente de código no ambiente de desenvolvimento do Visual Studio, ele adicionará um [ \<resumo >](../../../visual-basic/language-reference/xmldoc/summary.md) marca para a nova propriedade.</span><span class="sxs-lookup"><span data-stu-id="e62a0-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="e62a0-110">Você deve adicionar manualmente um `<value>` marca para descrever o valor que representa a propriedade.</span><span class="sxs-lookup"><span data-stu-id="e62a0-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="e62a0-111">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="e62a0-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e62a0-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e62a0-112">Example</span></span>  
 <span data-ttu-id="e62a0-113">Este exemplo usa o `<value>` marca para descrever qual valor o `Counter` isenções de propriedade.</span><span class="sxs-lookup"><span data-stu-id="e62a0-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e62a0-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e62a0-114">See also</span></span>
- [<span data-ttu-id="e62a0-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="e62a0-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
