---
title: '&lt;código&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 9ec9d23f1f62358dc272f9764f88e3bb2ba41f78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599746"
---
# <a name="ltcodegt-visual-basic"></a><span data-ttu-id="3d9f1-102">&lt;código&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d9f1-102">&lt;code&gt; (Visual Basic)</span></span>
<span data-ttu-id="3d9f1-103">Indica que o texto tem várias linhas de código.</span><span class="sxs-lookup"><span data-stu-id="3d9f1-103">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d9f1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d9f1-104">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d9f1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3d9f1-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="3d9f1-106">O texto para marcar como código.</span><span class="sxs-lookup"><span data-stu-id="3d9f1-106">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d9f1-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3d9f1-107">Remarks</span></span>  
 <span data-ttu-id="3d9f1-108">Use o `<code>` marca para indicar várias linhas como código.</span><span class="sxs-lookup"><span data-stu-id="3d9f1-108">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="3d9f1-109">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) para indicar que o texto dentro uma descrição deve ser marcado como código.</span><span class="sxs-lookup"><span data-stu-id="3d9f1-109">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="3d9f1-110">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="3d9f1-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d9f1-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3d9f1-111">Example</span></span>  
 <span data-ttu-id="3d9f1-112">Este exemplo usa o \<código > marca para incluir o código de exemplo para usar o `ID` campo.</span><span class="sxs-lookup"><span data-stu-id="3d9f1-112">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3d9f1-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d9f1-113">See Also</span></span>  
 [<span data-ttu-id="3d9f1-114">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="3d9f1-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
