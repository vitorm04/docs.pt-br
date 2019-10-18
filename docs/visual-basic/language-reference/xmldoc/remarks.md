---
title: <remarks> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 38549b2fcce0740b2b9cfd42d950e56b343e7a30
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524667"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="d1a0c-102">> de \<remarks (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1a0c-102">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="d1a0c-103">Especifica uma seção de comentários para o membro.</span><span class="sxs-lookup"><span data-stu-id="d1a0c-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1a0c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1a0c-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1a0c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d1a0c-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="d1a0c-106">Uma descrição do membro.</span><span class="sxs-lookup"><span data-stu-id="d1a0c-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1a0c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d1a0c-107">Remarks</span></span>  
 <span data-ttu-id="d1a0c-108">Use a marca `<remarks>` para adicionar informações sobre um tipo, complementando as informações especificadas com [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="d1a0c-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="d1a0c-109">Essas informações são exibidas no Pesquisador de objetos.</span><span class="sxs-lookup"><span data-stu-id="d1a0c-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="d1a0c-110">Para obter informações sobre o pesquisador de objetos, consulte [exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="d1a0c-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="d1a0c-111">Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="d1a0c-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1a0c-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d1a0c-112">Example</span></span>  
 <span data-ttu-id="d1a0c-113">Este exemplo usa a marca `<remarks>` para explicar o que o método `UpdateRecord` faz.</span><span class="sxs-lookup"><span data-stu-id="d1a0c-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="d1a0c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1a0c-114">See also</span></span>

- [<span data-ttu-id="d1a0c-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="d1a0c-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
