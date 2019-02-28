---
title: <exception> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 157287ce5c85ec51f1711934cf9a5e4f568957ef
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977167"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="6fb62-102">\<exceção > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fb62-102">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="6fb62-103">Especifica quais exceções podem ser geradas.</span><span class="sxs-lookup"><span data-stu-id="6fb62-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fb62-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fb62-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6fb62-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6fb62-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="6fb62-106">Uma referência a uma exceção que está disponível no ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="6fb62-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="6fb62-107">O compilador verifica se a exceção apresentada existe e move o `member` para o nome de elemento canônico no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="6fb62-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="6fb62-108">`member` deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="6fb62-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="6fb62-109">Uma descrição.</span><span class="sxs-lookup"><span data-stu-id="6fb62-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fb62-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="6fb62-110">Remarks</span></span>  
 <span data-ttu-id="6fb62-111">Use o `<exception>` marca para especificar quais exceções podem ser geradas.</span><span class="sxs-lookup"><span data-stu-id="6fb62-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="6fb62-112">Essa marcação é aplicada a uma definição de método.</span><span class="sxs-lookup"><span data-stu-id="6fb62-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="6fb62-113">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="6fb62-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fb62-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6fb62-114">Example</span></span>  
 <span data-ttu-id="6fb62-115">Este exemplo usa o `<exception>` marca para descrever uma exceção que o `IntDivide` função pode gerar.</span><span class="sxs-lookup"><span data-stu-id="6fb62-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="6fb62-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fb62-116">See also</span></span>
- [<span data-ttu-id="6fb62-117">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="6fb62-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
