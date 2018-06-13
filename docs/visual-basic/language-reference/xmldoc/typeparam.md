---
title: '&lt;typeparam&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 76e0e8d4757f29bb5df82ea1482beff3dd43c0e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598008"
---
# <a name="lttypeparamgt-visual-basic"></a><span data-ttu-id="78eb1-102">&lt;typeparam&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78eb1-102">&lt;typeparam&gt; (Visual Basic)</span></span>
<span data-ttu-id="78eb1-103">Define um nome de parâmetro de tipo e descrição.</span><span class="sxs-lookup"><span data-stu-id="78eb1-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78eb1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78eb1-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78eb1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="78eb1-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="78eb1-106">O nome do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="78eb1-106">The name of the type parameter.</span></span> <span data-ttu-id="78eb1-107">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="78eb1-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="78eb1-108">Uma descrição do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="78eb1-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78eb1-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="78eb1-109">Remarks</span></span>  
 <span data-ttu-id="78eb1-110">Use o `<typeparam>` marca de comentário para um tipo genérico ou declaração de membro genérico descrever um dos parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="78eb1-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="78eb1-111">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="78eb1-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78eb1-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="78eb1-112">Example</span></span>  
 <span data-ttu-id="78eb1-113">Este exemplo usa o `<typeparam>` marcas para descrever o `id` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="78eb1-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="78eb1-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78eb1-114">See Also</span></span>  
 [<span data-ttu-id="78eb1-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="78eb1-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
