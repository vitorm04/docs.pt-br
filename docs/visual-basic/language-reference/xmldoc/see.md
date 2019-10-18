---
title: <see> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: e3ae5fb63540e47e5b8da2e2d60d5bd736e019d7
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524664"
---
# <a name="see-visual-basic"></a><span data-ttu-id="ca618-102">> de \<see (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca618-102">\<see> (Visual Basic)</span></span>
<span data-ttu-id="ca618-103">Especifica um link para outro membro.</span><span class="sxs-lookup"><span data-stu-id="ca618-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca618-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca618-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca618-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca618-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="ca618-106">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="ca618-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="ca618-107">O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="ca618-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="ca618-108">`member` deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="ca618-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca618-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca618-109">Remarks</span></span>  
 <span data-ttu-id="ca618-110">Use a marca `<see>` para especificar um link de dentro do texto.</span><span class="sxs-lookup"><span data-stu-id="ca618-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="ca618-111">Use [\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) para indicar o texto que você pode querer que apareça em uma seção "Veja também".</span><span class="sxs-lookup"><span data-stu-id="ca618-111">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="ca618-112">Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="ca618-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca618-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ca618-113">Example</span></span>  
 <span data-ttu-id="ca618-114">Este exemplo usa a marca `<see>` na seção `UpdateRecord` comentários para fazer referência ao método `DoesRecordExist`.</span><span class="sxs-lookup"><span data-stu-id="ca618-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="ca618-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca618-115">See also</span></span>

- [<span data-ttu-id="ca618-116">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="ca618-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
