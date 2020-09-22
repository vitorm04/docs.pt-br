---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 471d3ddb5cf5a234cb77de6d1d93309faf754359
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90865836"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="9ee9d-101">\<summary> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ee9d-101">\<summary> (Visual Basic)</span></span>

<span data-ttu-id="9ee9d-102">Especifica o resumo do membro.</span><span class="sxs-lookup"><span data-stu-id="9ee9d-102">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ee9d-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ee9d-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ee9d-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9ee9d-104">Parameters</span></span>  

 `description`  
 <span data-ttu-id="9ee9d-105">Um resumo do objeto.</span><span class="sxs-lookup"><span data-stu-id="9ee9d-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ee9d-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="9ee9d-106">Remarks</span></span>  

 <span data-ttu-id="9ee9d-107">Use a `<summary>` marca para descrever um tipo ou um membro de tipo.</span><span class="sxs-lookup"><span data-stu-id="9ee9d-107">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="9ee9d-108">Use [\<remarks>](remarks.md) para adicionar informações complementares a uma descrição de tipo.</span><span class="sxs-lookup"><span data-stu-id="9ee9d-108">Use [\<remarks>](remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="9ee9d-109">O texto da `<summary>` marca é a única fonte de informações sobre o tipo no IntelliSense e também é exibido no Pesquisador de objetos.</span><span class="sxs-lookup"><span data-stu-id="9ee9d-109">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="9ee9d-110">Para obter informações sobre o pesquisador de objetos, consulte [exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="9ee9d-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="9ee9d-111">Compile com [-Doc](../../reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="9ee9d-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ee9d-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ee9d-112">Example</span></span>  

 <span data-ttu-id="9ee9d-113">Este exemplo usa a `<summary>` marca para descrever o `ResetCounter` método e a `Counter` propriedade.</span><span class="sxs-lookup"><span data-stu-id="9ee9d-113">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9ee9d-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="9ee9d-114">See also</span></span>

- [<span data-ttu-id="9ee9d-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="9ee9d-115">XML Comment Tags</span></span>](index.md)
