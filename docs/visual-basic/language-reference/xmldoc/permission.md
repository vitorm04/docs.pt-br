---
title: <permission>
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: b3acec04060367a0b9e54b19c0106644d028357b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400028"
---
# <a name="permission-visual-basic"></a><span data-ttu-id="7491c-101">\<permission> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7491c-101">\<permission> (Visual Basic)</span></span>
<span data-ttu-id="7491c-102">Especifica uma permissão necessária para o membro.</span><span class="sxs-lookup"><span data-stu-id="7491c-102">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7491c-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7491c-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="7491c-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7491c-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="7491c-105">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="7491c-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="7491c-106">O compilador verifica se o elemento de código fornecido existe e converte `member` no nome de elemento canônico no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="7491c-106">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="7491c-107">Coloque `member` entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="7491c-107">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="7491c-108">Uma descrição do acesso ao membro.</span><span class="sxs-lookup"><span data-stu-id="7491c-108">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7491c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="7491c-109">Remarks</span></span>  
 <span data-ttu-id="7491c-110">Use a `<permission>` marca para documentar o acesso de um membro.</span><span class="sxs-lookup"><span data-stu-id="7491c-110">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="7491c-111">Use a <xref:System.Security.PermissionSet> classe para especificar o acesso a um membro.</span><span class="sxs-lookup"><span data-stu-id="7491c-111">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="7491c-112">Compile com [-Doc](../../reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="7491c-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7491c-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7491c-113">Example</span></span>  
 <span data-ttu-id="7491c-114">Este exemplo usa a `<permission>` marca para descrever que o <xref:System.Security.Permissions.FileIOPermission> é exigido pelo `ReadFile` método.</span><span class="sxs-lookup"><span data-stu-id="7491c-114">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="7491c-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="7491c-115">See also</span></span>

- [<span data-ttu-id="7491c-116">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="7491c-116">XML Comment Tags</span></span>](index.md)
