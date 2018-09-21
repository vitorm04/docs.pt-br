---
title: '&lt;permissão&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: bcec5d968f5d0c5400c28e772df151b164888a47
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46539519"
---
# <a name="ltpermissiongt-visual-basic"></a><span data-ttu-id="2a96d-102">&lt;permissão&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a96d-102">&lt;permission&gt; (Visual Basic)</span></span>
<span data-ttu-id="2a96d-103">Especifica uma permissão necessária para o membro.</span><span class="sxs-lookup"><span data-stu-id="2a96d-103">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a96d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a96d-104">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a96d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2a96d-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="2a96d-106">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="2a96d-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="2a96d-107">O compilador verifica se o elemento de código fornecido existe e converte `member` no nome de elemento canônico no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="2a96d-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="2a96d-108">Coloque `member` entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="2a96d-108">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="2a96d-109">Uma descrição do acesso ao membro.</span><span class="sxs-lookup"><span data-stu-id="2a96d-109">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a96d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a96d-110">Remarks</span></span>  
 <span data-ttu-id="2a96d-111">Use o `<permission>` marca para documentar o acesso de um membro.</span><span class="sxs-lookup"><span data-stu-id="2a96d-111">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="2a96d-112">Use o <xref:System.Security.PermissionSet> classe para especificar o acesso a um membro.</span><span class="sxs-lookup"><span data-stu-id="2a96d-112">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="2a96d-113">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="2a96d-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a96d-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a96d-114">Example</span></span>  
 <span data-ttu-id="2a96d-115">Este exemplo usa o `<permission>` marca para descrever o que o <xref:System.Security.Permissions.FileIOPermission> é necessária para o `ReadFile` método.</span><span class="sxs-lookup"><span data-stu-id="2a96d-115">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2a96d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a96d-116">See Also</span></span>  
 [<span data-ttu-id="2a96d-117">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="2a96d-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
