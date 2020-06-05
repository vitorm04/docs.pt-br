---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: c57ddb870192bd94301f99eb71ad29526e8efc28
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400015"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="2360a-101">\<remarks> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2360a-101">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="2360a-102">Especifica uma seção de comentários para o membro.</span><span class="sxs-lookup"><span data-stu-id="2360a-102">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2360a-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2360a-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="2360a-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2360a-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="2360a-105">Uma descrição do membro.</span><span class="sxs-lookup"><span data-stu-id="2360a-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2360a-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="2360a-106">Remarks</span></span>  
 <span data-ttu-id="2360a-107">Use a `<remarks>` marca para adicionar informações sobre um tipo, complementando as informações especificadas com [\<summary>](summary.md) .</span><span class="sxs-lookup"><span data-stu-id="2360a-107">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](summary.md).</span></span>  
  
 <span data-ttu-id="2360a-108">Essas informações são exibidas no Pesquisador de objetos.</span><span class="sxs-lookup"><span data-stu-id="2360a-108">This information appears in the Object Browser.</span></span> <span data-ttu-id="2360a-109">Para obter informações sobre o pesquisador de objetos, consulte [exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="2360a-109">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="2360a-110">Compile com [-Doc](../../reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="2360a-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2360a-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2360a-111">Example</span></span>  
 <span data-ttu-id="2360a-112">Este exemplo usa a `<remarks>` marca para explicar o que o `UpdateRecord` método faz.</span><span class="sxs-lookup"><span data-stu-id="2360a-112">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="2360a-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="2360a-113">See also</span></span>

- [<span data-ttu-id="2360a-114">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="2360a-114">XML Comment Tags</span></span>](index.md)
