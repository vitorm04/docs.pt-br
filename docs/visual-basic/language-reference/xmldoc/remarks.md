---
title: <remarks> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: c5c088472ae09a416953d9c0829cad1cb48646b8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833484"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="69225-102">\<Remarks > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69225-102">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="69225-103">Especifica uma seção de comentários para o membro.</span><span class="sxs-lookup"><span data-stu-id="69225-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69225-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69225-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="69225-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69225-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="69225-106">Uma descrição do membro.</span><span class="sxs-lookup"><span data-stu-id="69225-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69225-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="69225-107">Remarks</span></span>  
 <span data-ttu-id="69225-108">Use o `<remarks>` marca para adicionar informações sobre um tipo, complementando as informações especificadas com [ \<resumo >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="69225-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="69225-109">Essas informações são exibidas no Pesquisador de objetos.</span><span class="sxs-lookup"><span data-stu-id="69225-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="69225-110">Para obter informações sobre o Pesquisador de objetos, consulte [exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="69225-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="69225-111">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="69225-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69225-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69225-112">Example</span></span>  
 <span data-ttu-id="69225-113">Este exemplo usa o `<remarks>` marca para explicar o que o `UpdateRecord` que o método.</span><span class="sxs-lookup"><span data-stu-id="69225-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="69225-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69225-114">See also</span></span>

- [<span data-ttu-id="69225-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="69225-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
