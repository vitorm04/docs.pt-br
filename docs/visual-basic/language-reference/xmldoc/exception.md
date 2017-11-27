---
title: "&lt;exceção&gt; (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d718a7c2213a61f7f60ed80a04f9bd03f6c770a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltexceptiongt-visual-basic"></a><span data-ttu-id="fc1b2-102">&lt;exceção&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc1b2-102">&lt;exception&gt; (Visual Basic)</span></span>
<span data-ttu-id="fc1b2-103">Especifica quais exceções podem ser geradas.</span><span class="sxs-lookup"><span data-stu-id="fc1b2-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc1b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc1b2-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc1b2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fc1b2-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="fc1b2-106">Uma referência a uma exceção que está disponível no ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="fc1b2-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="fc1b2-107">O compilador verifica se a exceção apresentada existe e move o `member` para o nome de elemento canônico no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="fc1b2-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="fc1b2-108">`member` deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="fc1b2-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="fc1b2-109">Uma descrição.</span><span class="sxs-lookup"><span data-stu-id="fc1b2-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc1b2-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="fc1b2-110">Remarks</span></span>  
 <span data-ttu-id="fc1b2-111">Use o `<exception>` marca para especificar quais exceções podem ser geradas.</span><span class="sxs-lookup"><span data-stu-id="fc1b2-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="fc1b2-112">Essa marca é aplicada a uma definição de método.</span><span class="sxs-lookup"><span data-stu-id="fc1b2-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="fc1b2-113">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="fc1b2-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc1b2-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fc1b2-114">Example</span></span>  
 <span data-ttu-id="fc1b2-115">Este exemplo usa o `<exception>` marcas para descrever uma exceção que o `IntDivide` pode lançar uma função.</span><span class="sxs-lookup"><span data-stu-id="fc1b2-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fc1b2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc1b2-116">See Also</span></span>  
 [<span data-ttu-id="fc1b2-117">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="fc1b2-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
