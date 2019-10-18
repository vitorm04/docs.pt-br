---
title: <typeparam> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: dbd99997fed33c192a2160fb45a739addbae254a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524626"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="6e043-102">> de \<typeparam (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e043-102">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="6e043-103">Define um nome de parâmetro de tipo e uma descrição.</span><span class="sxs-lookup"><span data-stu-id="6e043-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e043-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e043-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e043-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e043-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="6e043-106">O nome do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="6e043-106">The name of the type parameter.</span></span> <span data-ttu-id="6e043-107">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="6e043-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="6e043-108">Uma descrição do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="6e043-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e043-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e043-109">Remarks</span></span>  
 <span data-ttu-id="6e043-110">Use a marca `<typeparam>` no comentário para um tipo genérico ou declaração de membro genérico para descrever um dos parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="6e043-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="6e043-111">Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="6e043-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e043-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6e043-112">Example</span></span>  
 <span data-ttu-id="6e043-113">Este exemplo usa a marca `<typeparam>` para descrever o parâmetro `id`.</span><span class="sxs-lookup"><span data-stu-id="6e043-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="6e043-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e043-114">See also</span></span>

- [<span data-ttu-id="6e043-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="6e043-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
