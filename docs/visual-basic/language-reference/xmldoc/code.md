---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: d058663213cf02f2142bff740aeec1b60791362c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873029"
---
# <a name="code-visual-basic"></a><span data-ttu-id="007b4-101">\<code> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="007b4-101">\<code> (Visual Basic)</span></span>

<span data-ttu-id="007b4-102">Indica que o texto tem várias linhas de código.</span><span class="sxs-lookup"><span data-stu-id="007b4-102">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="007b4-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="007b4-103">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a><span data-ttu-id="007b4-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="007b4-104">Parameters</span></span>  

 `content`  
 <span data-ttu-id="007b4-105">O texto a ser marcado como código.</span><span class="sxs-lookup"><span data-stu-id="007b4-105">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="007b4-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="007b4-106">Remarks</span></span>  

 <span data-ttu-id="007b4-107">Use a `<code>` marca para indicar várias linhas como código.</span><span class="sxs-lookup"><span data-stu-id="007b4-107">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="007b4-108">Use [\<c>](c.md) para indicar que o texto dentro de uma descrição deve ser marcado como código.</span><span class="sxs-lookup"><span data-stu-id="007b4-108">Use [\<c>](c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="007b4-109">Compile com [-Doc](../../reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="007b4-109">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="007b4-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="007b4-110">Example</span></span>  

 <span data-ttu-id="007b4-111">Este exemplo usa a \<code> marca para incluir o código de exemplo para usar o `ID` campo.</span><span class="sxs-lookup"><span data-stu-id="007b4-111">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="007b4-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="007b4-112">See also</span></span>

- [<span data-ttu-id="007b4-113">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="007b4-113">XML Comment Tags</span></span>](index.md)
