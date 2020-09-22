---
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: e3f386d2a1e15ea3e1519d6e1e5e31c34c73fb99
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872902"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="aa49e-101">\<exception> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa49e-101">\<exception> (Visual Basic)</span></span>

<span data-ttu-id="aa49e-102">Especifica quais exceções podem ser geradas.</span><span class="sxs-lookup"><span data-stu-id="aa49e-102">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa49e-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa49e-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa49e-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa49e-104">Parameters</span></span>  

 `member`  
 <span data-ttu-id="aa49e-105">Uma referência a uma exceção que está disponível no ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="aa49e-105">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="aa49e-106">O compilador verifica se a exceção apresentada existe e move o `member` para o nome de elemento canônico no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="aa49e-106">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="aa49e-107">`member` deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="aa49e-107">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="aa49e-108">Uma descrição.</span><span class="sxs-lookup"><span data-stu-id="aa49e-108">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa49e-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa49e-109">Remarks</span></span>  

 <span data-ttu-id="aa49e-110">Use a `<exception>` marca para especificar quais exceções podem ser geradas.</span><span class="sxs-lookup"><span data-stu-id="aa49e-110">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="aa49e-111">Essa marcação é aplicada a uma definição de método.</span><span class="sxs-lookup"><span data-stu-id="aa49e-111">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="aa49e-112">Compile com [-Doc](../../reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="aa49e-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa49e-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa49e-113">Example</span></span>  

 <span data-ttu-id="aa49e-114">Este exemplo usa a `<exception>` marca para descrever uma exceção que a `IntDivide` função pode gerar.</span><span class="sxs-lookup"><span data-stu-id="aa49e-114">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="aa49e-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="aa49e-115">See also</span></span>

- [<span data-ttu-id="aa49e-116">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="aa49e-116">XML Comment Tags</span></span>](index.md)
