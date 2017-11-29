---
title: "&lt;código&gt; (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a7c1d8ab3db0c36c6a2935b9ffbef15e87df5ebc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcodegt-visual-basic"></a><span data-ttu-id="553f5-102">&lt;código&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="553f5-102">&lt;code&gt; (Visual Basic)</span></span>
<span data-ttu-id="553f5-103">Indica que o texto tem várias linhas de código.</span><span class="sxs-lookup"><span data-stu-id="553f5-103">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="553f5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="553f5-104">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="553f5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="553f5-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="553f5-106">O texto para marcar como código.</span><span class="sxs-lookup"><span data-stu-id="553f5-106">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="553f5-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="553f5-107">Remarks</span></span>  
 <span data-ttu-id="553f5-108">Use o `<code>` marca para indicar várias linhas como código.</span><span class="sxs-lookup"><span data-stu-id="553f5-108">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="553f5-109">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) para indicar que o texto dentro uma descrição deve ser marcado como código.</span><span class="sxs-lookup"><span data-stu-id="553f5-109">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="553f5-110">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="553f5-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="553f5-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="553f5-111">Example</span></span>  
 <span data-ttu-id="553f5-112">Este exemplo usa o \<código > marca para incluir o código de exemplo para usar o `ID` campo.</span><span class="sxs-lookup"><span data-stu-id="553f5-112">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="553f5-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="553f5-113">See Also</span></span>  
 [<span data-ttu-id="553f5-114">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="553f5-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
