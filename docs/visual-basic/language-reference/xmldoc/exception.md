---
title: <exception> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 16ffb4f6b57dabb3650376c913a7d7608a00646d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523924"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="28471-102">> de \<exception (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28471-102">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="28471-103">Especifica quais exceções podem ser geradas.</span><span class="sxs-lookup"><span data-stu-id="28471-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28471-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28471-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="28471-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="28471-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="28471-106">Uma referência a uma exceção que está disponível no ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="28471-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="28471-107">O compilador verifica se a exceção apresentada existe e move o `member` para o nome de elemento canônico no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="28471-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="28471-108">`member` deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="28471-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="28471-109">Uma descrição.</span><span class="sxs-lookup"><span data-stu-id="28471-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28471-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="28471-110">Remarks</span></span>  
 <span data-ttu-id="28471-111">Use a marca `<exception>` para especificar quais exceções podem ser geradas.</span><span class="sxs-lookup"><span data-stu-id="28471-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="28471-112">Essa marcação é aplicada a uma definição de método.</span><span class="sxs-lookup"><span data-stu-id="28471-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="28471-113">Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="28471-113">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28471-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="28471-114">Example</span></span>  
 <span data-ttu-id="28471-115">Este exemplo usa a marca `<exception>` para descrever uma exceção que a função `IntDivide` pode gerar.</span><span class="sxs-lookup"><span data-stu-id="28471-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="28471-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28471-116">See also</span></span>

- [<span data-ttu-id="28471-117">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="28471-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
