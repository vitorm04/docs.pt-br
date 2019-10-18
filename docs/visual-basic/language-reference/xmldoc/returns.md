---
title: <returns> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: b220c2a9aa544413c3692485f6c1eb2b64e54389
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524689"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="0fb05-102">> de \<returns (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fb05-102">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="0fb05-103">Especifica o valor de retorno da propriedade ou função.</span><span class="sxs-lookup"><span data-stu-id="0fb05-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fb05-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0fb05-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fb05-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0fb05-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="0fb05-106">Uma descrição do valor retornado.</span><span class="sxs-lookup"><span data-stu-id="0fb05-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fb05-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="0fb05-107">Remarks</span></span>  
 <span data-ttu-id="0fb05-108">Use a marca `<returns>` no comentário para uma declaração de método para descrever o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="0fb05-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="0fb05-109">Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="0fb05-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fb05-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0fb05-110">Example</span></span>  
 <span data-ttu-id="0fb05-111">Este exemplo usa a marca `<returns>` para explicar o que a função `DoesRecordExist` retorna.</span><span class="sxs-lookup"><span data-stu-id="0fb05-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="0fb05-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0fb05-112">See also</span></span>

- [<span data-ttu-id="0fb05-113">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="0fb05-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
