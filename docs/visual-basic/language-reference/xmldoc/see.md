---
title: <see>
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 51eaaef2ddb88afbb52ab58b85ed1a58ba251c1e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866456"
---
# <a name="see-visual-basic"></a><span data-ttu-id="cd716-101">\<see> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd716-101">\<see> (Visual Basic)</span></span>

<span data-ttu-id="cd716-102">Especifica um link para outro membro.</span><span class="sxs-lookup"><span data-stu-id="cd716-102">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd716-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd716-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd716-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cd716-104">Parameters</span></span>  

 `member`  
 <span data-ttu-id="cd716-105">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="cd716-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="cd716-106">O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="cd716-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="cd716-107">`member` deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="cd716-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd716-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="cd716-108">Remarks</span></span>  

 <span data-ttu-id="cd716-109">Use a `<see>` marca para especificar um link de dentro do texto.</span><span class="sxs-lookup"><span data-stu-id="cd716-109">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="cd716-110">Use [\<seealso>](seealso.md) para indicar o texto que você pode querer que apareça em uma seção "Veja também".</span><span class="sxs-lookup"><span data-stu-id="cd716-110">Use [\<seealso>](seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="cd716-111">Compile com [-Doc](../../reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="cd716-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd716-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd716-112">Example</span></span>  

 <span data-ttu-id="cd716-113">Este exemplo usa a `<see>` marca na `UpdateRecord` seção comentários para fazer referência ao `DoesRecordExist` método.</span><span class="sxs-lookup"><span data-stu-id="cd716-113">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="cd716-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="cd716-114">See also</span></span>

- [<span data-ttu-id="cd716-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="cd716-115">XML Comment Tags</span></span>](index.md)
