---
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 37b110cc6e12f11196d2a1c5cc6026d87b453626
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866393"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="d1e49-101">\<returns> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1e49-101">\<returns> (Visual Basic)</span></span>

<span data-ttu-id="d1e49-102">Especifica o valor de retorno da propriedade ou função.</span><span class="sxs-lookup"><span data-stu-id="d1e49-102">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1e49-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1e49-103">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1e49-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d1e49-104">Parameters</span></span>  

 `description`  
 <span data-ttu-id="d1e49-105">Uma descrição do valor retornado.</span><span class="sxs-lookup"><span data-stu-id="d1e49-105">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1e49-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="d1e49-106">Remarks</span></span>  

 <span data-ttu-id="d1e49-107">Use a `<returns>` marca no comentário para uma declaração de método para descrever o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="d1e49-107">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="d1e49-108">Compile com [-Doc](../../reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="d1e49-108">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1e49-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d1e49-109">Example</span></span>  

 <span data-ttu-id="d1e49-110">Este exemplo usa a `<returns>` marca para explicar o que a `DoesRecordExist` função retorna.</span><span class="sxs-lookup"><span data-stu-id="d1e49-110">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="d1e49-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="d1e49-111">See also</span></span>

- [<span data-ttu-id="d1e49-112">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="d1e49-112">XML Comment Tags</span></span>](index.md)
