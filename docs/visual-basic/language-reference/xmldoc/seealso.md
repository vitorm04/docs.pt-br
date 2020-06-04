---
title: <seealso>
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 5999a4ebcc90f21ee8331b96ffb2a50f7905b1b6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411506"
---
# <a name="seealso-visual-basic"></a><span data-ttu-id="de168-101">\<seealso> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de168-101">\<seealso> (Visual Basic)</span></span>
<span data-ttu-id="de168-102">Especifica um link que aparece na seção Consulte também.</span><span class="sxs-lookup"><span data-stu-id="de168-102">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de168-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de168-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="de168-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="de168-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="de168-105">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="de168-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="de168-106">O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="de168-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="de168-107">`member` deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="de168-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de168-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="de168-108">Remarks</span></span>  
 <span data-ttu-id="de168-109">Use a `<seealso>` marca para especificar o texto que você deseja que apareça em uma seção ver também.</span><span class="sxs-lookup"><span data-stu-id="de168-109">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="de168-110">Use [\<see>](see.md) para especificar um link de dentro do texto.</span><span class="sxs-lookup"><span data-stu-id="de168-110">Use [\<see>](see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="de168-111">Compile com [-Doc](../../reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="de168-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de168-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="de168-112">Example</span></span>  
 <span data-ttu-id="de168-113">Este exemplo usa a `<seealso>` marca na `DoesRecordExist` seção comentários para fazer referência ao `UpdateRecord` método.</span><span class="sxs-lookup"><span data-stu-id="de168-113">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="de168-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="de168-114">See also</span></span>

- [<span data-ttu-id="de168-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="de168-115">XML Comment Tags</span></span>](index.md)
