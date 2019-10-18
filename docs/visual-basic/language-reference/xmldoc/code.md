---
title: <code> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: d4e887e3bbbc01e4cef5278f67b8c4afe273bf28
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524039"
---
# <a name="code-visual-basic"></a><span data-ttu-id="2d54d-101">> de \<code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d54d-101">\<code> (Visual Basic)</span></span>
<span data-ttu-id="2d54d-102">Indica que o texto tem várias linhas de código.</span><span class="sxs-lookup"><span data-stu-id="2d54d-102">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d54d-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d54d-103">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d54d-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2d54d-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="2d54d-105">O texto a ser marcado como código.</span><span class="sxs-lookup"><span data-stu-id="2d54d-105">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d54d-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="2d54d-106">Remarks</span></span>  
 <span data-ttu-id="2d54d-107">Use a marca `<code>` para indicar várias linhas como código.</span><span class="sxs-lookup"><span data-stu-id="2d54d-107">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="2d54d-108">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) para indicar que o texto dentro uma descrição deve ser marcado como código.</span><span class="sxs-lookup"><span data-stu-id="2d54d-108">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="2d54d-109">Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="2d54d-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d54d-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2d54d-110">Example</span></span>  
 <span data-ttu-id="2d54d-111">Este exemplo usa a marca de > \<code para incluir código de exemplo para usar o campo `ID`.</span><span class="sxs-lookup"><span data-stu-id="2d54d-111">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2d54d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d54d-112">See also</span></span>

- [<span data-ttu-id="2d54d-113">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="2d54d-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
