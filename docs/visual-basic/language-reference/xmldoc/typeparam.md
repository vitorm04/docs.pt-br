---
title: <typeparam> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: d7fb980545a532e39310ea3e9d663a2b5a81a006
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968446"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="677f6-102">\<typeparam > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="677f6-102">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="677f6-103">Define um nome de parâmetro de tipo e uma descrição.</span><span class="sxs-lookup"><span data-stu-id="677f6-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="677f6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="677f6-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="677f6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="677f6-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="677f6-106">O nome do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="677f6-106">The name of the type parameter.</span></span> <span data-ttu-id="677f6-107">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="677f6-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="677f6-108">Uma descrição do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="677f6-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="677f6-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="677f6-109">Remarks</span></span>  
 <span data-ttu-id="677f6-110">Use o `<typeparam>` marca no comentário para um tipo genérico ou declaração de membro genérico descrever um dos parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="677f6-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="677f6-111">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="677f6-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="677f6-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="677f6-112">Example</span></span>  
 <span data-ttu-id="677f6-113">Este exemplo usa o `<typeparam>` marca para descrever o `id` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="677f6-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="677f6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="677f6-114">See also</span></span>
- [<span data-ttu-id="677f6-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="677f6-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
