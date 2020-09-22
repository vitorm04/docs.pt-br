---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 550f8b63928f80878ba316bfaf09077e14091305
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875174"
---
# <a name="value-visual-basic"></a><span data-ttu-id="750fe-101">\<value> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="750fe-101">\<value> (Visual Basic)</span></span>

<span data-ttu-id="750fe-102">Especifica a descrição de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="750fe-102">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="750fe-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="750fe-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="750fe-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="750fe-104">Parameters</span></span>  

 `property-description`  
 <span data-ttu-id="750fe-105">Uma descrição da propriedade.</span><span class="sxs-lookup"><span data-stu-id="750fe-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="750fe-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="750fe-106">Remarks</span></span>  

 <span data-ttu-id="750fe-107">Use a `<value>` marca para descrever uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="750fe-107">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="750fe-108">Observe que quando você adiciona uma propriedade usando o assistente de código no ambiente de desenvolvimento do Visual Studio, ela adicionará uma [\<summary>](summary.md) marca para a nova propriedade.</span><span class="sxs-lookup"><span data-stu-id="750fe-108">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](summary.md) tag for the new property.</span></span> <span data-ttu-id="750fe-109">Em seguida, você deve adicionar manualmente uma `<value>` marca para descrever o valor que a propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="750fe-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="750fe-110">Compile com [-Doc](../../reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="750fe-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="750fe-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="750fe-111">Example</span></span>  

 <span data-ttu-id="750fe-112">Este exemplo usa a `<value>` marca para descrever o valor que a `Counter` Propriedade mantém.</span><span class="sxs-lookup"><span data-stu-id="750fe-112">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="750fe-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="750fe-113">See also</span></span>

- [<span data-ttu-id="750fe-114">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="750fe-114">XML Comment Tags</span></span>](index.md)
