---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 6e9f63e4d31df7790f51ae4d166b606f2c63f14b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872981"
---
# <a name="example-visual-basic"></a><span data-ttu-id="8a698-101">\<example> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a698-101">\<example> (Visual Basic)</span></span>

<span data-ttu-id="8a698-102">Especifica um exemplo para o membro.</span><span class="sxs-lookup"><span data-stu-id="8a698-102">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a698-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a698-103">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a698-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8a698-104">Parameters</span></span>  

 `description`  
 <span data-ttu-id="8a698-105">Uma descrição do exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="8a698-105">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a698-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a698-106">Remarks</span></span>  

 <span data-ttu-id="8a698-107">A `<example>` marca permite especificar um exemplo de como usar um método ou outro membro da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="8a698-107">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="8a698-108">Isso geralmente envolve o uso da [\<code>](code.md) marca.</span><span class="sxs-lookup"><span data-stu-id="8a698-108">This commonly involves using the [\<code>](code.md) tag.</span></span>  
  
 <span data-ttu-id="8a698-109">Compile com [-Doc](../../reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="8a698-109">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a698-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8a698-110">Example</span></span>  

 <span data-ttu-id="8a698-111">Este exemplo usa a `<example>` marca para incluir um exemplo para usar o `ID` campo.</span><span class="sxs-lookup"><span data-stu-id="8a698-111">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8a698-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="8a698-112">See also</span></span>

- [<span data-ttu-id="8a698-113">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="8a698-113">XML Comment Tags</span></span>](index.md)
