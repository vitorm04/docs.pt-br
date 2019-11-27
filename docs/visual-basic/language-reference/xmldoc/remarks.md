---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: b327e548bcdce1522a888855bd88e3150695147b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352256"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="ecc98-101">> de comentários do \<(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ecc98-101">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="ecc98-102">Especifica uma seção de comentários para o membro.</span><span class="sxs-lookup"><span data-stu-id="ecc98-102">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecc98-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ecc98-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecc98-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ecc98-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="ecc98-105">Uma descrição do membro.</span><span class="sxs-lookup"><span data-stu-id="ecc98-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecc98-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="ecc98-106">Remarks</span></span>  
 <span data-ttu-id="ecc98-107">Use a marca `<remarks>` para adicionar informações sobre um tipo, complementando as informações especificadas com [\<resumo >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="ecc98-107">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="ecc98-108">Essas informações são exibidas no Pesquisador de objetos.</span><span class="sxs-lookup"><span data-stu-id="ecc98-108">This information appears in the Object Browser.</span></span> <span data-ttu-id="ecc98-109">Para obter informações sobre o pesquisador de objetos, consulte [exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="ecc98-109">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="ecc98-110">Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="ecc98-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecc98-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ecc98-111">Example</span></span>  
 <span data-ttu-id="ecc98-112">Este exemplo usa a marca `<remarks>` para explicar o que o método `UpdateRecord` faz.</span><span class="sxs-lookup"><span data-stu-id="ecc98-112">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="ecc98-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ecc98-113">See also</span></span>

- [<span data-ttu-id="ecc98-114">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="ecc98-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
