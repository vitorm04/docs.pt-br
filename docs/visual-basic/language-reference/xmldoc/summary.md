---
title: <summary> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 25a0b307756401bed4d4c77d3668c2af53ba8b42
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524637"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="dfd35-102">> de \<summary (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dfd35-102">\<summary> (Visual Basic)</span></span>
<span data-ttu-id="dfd35-103">Especifica o resumo do membro.</span><span class="sxs-lookup"><span data-stu-id="dfd35-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfd35-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dfd35-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfd35-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dfd35-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="dfd35-106">Um resumo do objeto.</span><span class="sxs-lookup"><span data-stu-id="dfd35-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfd35-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="dfd35-107">Remarks</span></span>  
 <span data-ttu-id="dfd35-108">Use a marca `<summary>` para descrever um tipo ou um membro de tipo.</span><span class="sxs-lookup"><span data-stu-id="dfd35-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="dfd35-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) para adicionar mais informações a uma descrição de tipo.</span><span class="sxs-lookup"><span data-stu-id="dfd35-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="dfd35-110">O texto para a marca de `<summary>` é a única fonte de informações sobre o tipo no IntelliSense e também é exibido no Pesquisador de objetos.</span><span class="sxs-lookup"><span data-stu-id="dfd35-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="dfd35-111">Para obter informações sobre o pesquisador de objetos, consulte [exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="dfd35-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="dfd35-112">Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="dfd35-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfd35-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dfd35-113">Example</span></span>  
 <span data-ttu-id="dfd35-114">Este exemplo usa a marca `<summary>` para descrever o método `ResetCounter` e a propriedade `Counter`.</span><span class="sxs-lookup"><span data-stu-id="dfd35-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="dfd35-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfd35-115">See also</span></span>

- [<span data-ttu-id="dfd35-116">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="dfd35-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
