---
title: '&lt;typeparam&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: d362f181921a39d274eaee78e85976522ce4fc15
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863183"
---
# <a name="lttypeparamgt-visual-basic"></a><span data-ttu-id="ab544-102">&lt;typeparam&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab544-102">&lt;typeparam&gt; (Visual Basic)</span></span>
<span data-ttu-id="ab544-103">Define um nome de parâmetro de tipo e uma descrição.</span><span class="sxs-lookup"><span data-stu-id="ab544-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab544-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab544-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab544-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ab544-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="ab544-106">O nome do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="ab544-106">The name of the type parameter.</span></span> <span data-ttu-id="ab544-107">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="ab544-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="ab544-108">Uma descrição do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="ab544-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab544-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ab544-109">Remarks</span></span>  
 <span data-ttu-id="ab544-110">Use o `<typeparam>` marca no comentário para um tipo genérico ou declaração de membro genérico descrever um dos parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="ab544-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="ab544-111">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="ab544-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab544-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ab544-112">Example</span></span>  
 <span data-ttu-id="ab544-113">Este exemplo usa o `<typeparam>` marca para descrever o `id` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ab544-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ab544-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab544-114">See Also</span></span>  
 [<span data-ttu-id="ab544-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="ab544-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
