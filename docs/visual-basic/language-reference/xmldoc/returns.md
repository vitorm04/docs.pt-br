---
title: <returns> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 670064084d3297a54b2860da3fe3acab00fa3ed8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469177"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="c56f8-102">\<Retorna > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c56f8-102">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="c56f8-103">Especifica o valor de retorno da propriedade ou função.</span><span class="sxs-lookup"><span data-stu-id="c56f8-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c56f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c56f8-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="c56f8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c56f8-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="c56f8-106">Uma descrição do valor retornado.</span><span class="sxs-lookup"><span data-stu-id="c56f8-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c56f8-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c56f8-107">Remarks</span></span>  
 <span data-ttu-id="c56f8-108">Use o `<returns>` marca no comentário para uma declaração de método descrever o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="c56f8-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="c56f8-109">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="c56f8-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c56f8-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c56f8-110">Example</span></span>  
 <span data-ttu-id="c56f8-111">Este exemplo usa o `<returns>` marca para explicar o que o `DoesRecordExist` retornos de função.</span><span class="sxs-lookup"><span data-stu-id="c56f8-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="c56f8-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c56f8-112">See also</span></span>
- [<span data-ttu-id="c56f8-113">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="c56f8-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
