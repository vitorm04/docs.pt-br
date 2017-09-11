---
title: "&lt;exceção&gt; (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: 39d90b4465576fb5d4fed9420493e958e385667a
ms.contentlocale: pt-br
ms.lasthandoff: 06/01/2017

---
# <a name="ltexceptiongt-visual-basic"></a><span data-ttu-id="659fc-102">&lt;exceção&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="659fc-102">&lt;exception&gt; (Visual Basic)</span></span>
<span data-ttu-id="659fc-103">Especifica quais exceções podem ser geradas.</span><span class="sxs-lookup"><span data-stu-id="659fc-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="659fc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="659fc-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="659fc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="659fc-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="659fc-106">Uma referência a uma exceção que está disponível no ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="659fc-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="659fc-107">O compilador verifica se a exceção apresentada existe e converte `member` para o nome canônico de elemento na saída XML.</span><span class="sxs-lookup"><span data-stu-id="659fc-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="659fc-108">`member`deve aparecer entre aspas duplas ("").</span><span class="sxs-lookup"><span data-stu-id="659fc-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="659fc-109">Uma descrição.</span><span class="sxs-lookup"><span data-stu-id="659fc-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="659fc-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="659fc-110">Remarks</span></span>  
 <span data-ttu-id="659fc-111">Use o `<exception>` marca para especificar quais exceções podem ser geradas.</span><span class="sxs-lookup"><span data-stu-id="659fc-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="659fc-112">Essa marca é aplicada a uma definição de método.</span><span class="sxs-lookup"><span data-stu-id="659fc-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="659fc-113">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="659fc-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="659fc-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="659fc-114">Example</span></span>  
 <span data-ttu-id="659fc-115">Este exemplo usa o `<exception>` marca para descrever uma exceção que o `IntDivide` função pode gerar.</span><span class="sxs-lookup"><span data-stu-id="659fc-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 <span data-ttu-id="659fc-116">[!code-vb[VbVbcnXmlDocComments n º&3;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="659fc-116">[!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="659fc-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="659fc-117">See Also</span></span>  
 [<span data-ttu-id="659fc-118">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="659fc-118">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
