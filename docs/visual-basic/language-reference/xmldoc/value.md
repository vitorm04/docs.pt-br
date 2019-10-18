---
title: <value> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 516ff6ba534478d066b8ca06baee46bdd4b35265
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524610"
---
# <a name="value-visual-basic"></a><span data-ttu-id="b1ba6-102">> de \<value (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1ba6-102">\<value> (Visual Basic)</span></span>
<span data-ttu-id="b1ba6-103">Especifica a descrição de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="b1ba6-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1ba6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1ba6-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1ba6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1ba6-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="b1ba6-106">Uma descrição da propriedade.</span><span class="sxs-lookup"><span data-stu-id="b1ba6-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1ba6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1ba6-107">Remarks</span></span>  
 <span data-ttu-id="b1ba6-108">Use a marca `<value>` para descrever uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="b1ba6-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="b1ba6-109">Observe que quando você adiciona uma propriedade usando o assistente de código no ambiente de desenvolvimento do Visual Studio, ela adicionará um [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md) marca para a nova propriedade.</span><span class="sxs-lookup"><span data-stu-id="b1ba6-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="b1ba6-110">Em seguida, você deve adicionar manualmente uma marca de `<value>` para descrever o valor que a propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="b1ba6-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="b1ba6-111">Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="b1ba6-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1ba6-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1ba6-112">Example</span></span>  
 <span data-ttu-id="b1ba6-113">Este exemplo usa a marca `<value>` para descrever o valor que a propriedade `Counter` contém.</span><span class="sxs-lookup"><span data-stu-id="b1ba6-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b1ba6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1ba6-114">See also</span></span>

- [<span data-ttu-id="b1ba6-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="b1ba6-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
