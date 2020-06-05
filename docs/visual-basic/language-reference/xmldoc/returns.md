---
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: edbc374332bdcd67b385ac3d061045664e942460
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84399989"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="a1672-101">\<returns> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1672-101">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="a1672-102">Especifica o valor de retorno da propriedade ou função.</span><span class="sxs-lookup"><span data-stu-id="a1672-102">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1672-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1672-103">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1672-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a1672-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="a1672-105">Uma descrição do valor retornado.</span><span class="sxs-lookup"><span data-stu-id="a1672-105">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1672-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="a1672-106">Remarks</span></span>  
 <span data-ttu-id="a1672-107">Use a `<returns>` marca no comentário para uma declaração de método para descrever o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="a1672-107">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="a1672-108">Compile com [-Doc](../../reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="a1672-108">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1672-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a1672-109">Example</span></span>  
 <span data-ttu-id="a1672-110">Este exemplo usa a `<returns>` marca para explicar o que a `DoesRecordExist` função retorna.</span><span class="sxs-lookup"><span data-stu-id="a1672-110">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="a1672-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="a1672-111">See also</span></span>

- [<span data-ttu-id="a1672-112">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="a1672-112">XML Comment Tags</span></span>](index.md)
