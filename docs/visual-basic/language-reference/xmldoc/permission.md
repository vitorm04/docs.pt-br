---
title: "&lt;permissão&gt; (Visual Basic) | Documentos do Microsoft"
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
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
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
ms.openlocfilehash: ba033ccf4a4249cb06f1754968d4d2dfe0b90603
ms.contentlocale: pt-br
ms.lasthandoff: 06/01/2017

---
# <a name="ltpermissiongt-visual-basic"></a><span data-ttu-id="cb7d1-102">&lt;permissão&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb7d1-102">&lt;permission&gt; (Visual Basic)</span></span>
<span data-ttu-id="cb7d1-103">Especifica uma permissão necessária para o membro.</span><span class="sxs-lookup"><span data-stu-id="cb7d1-103">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb7d1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb7d1-104">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb7d1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cb7d1-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="cb7d1-106">Uma referência a um membro ou campo que está disponível para ser chamado a partir do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="cb7d1-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="cb7d1-107">O compilador verifica se o elemento de código fornecido existe e converte `member` para o nome canônico de elemento na saída XML.</span><span class="sxs-lookup"><span data-stu-id="cb7d1-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="cb7d1-108">Coloque `member` entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="cb7d1-108">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="cb7d1-109">Uma descrição do acesso ao membro.</span><span class="sxs-lookup"><span data-stu-id="cb7d1-109">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb7d1-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb7d1-110">Remarks</span></span>  
 <span data-ttu-id="cb7d1-111">Use o `<permission>` marca para documentar o acesso de um membro.</span><span class="sxs-lookup"><span data-stu-id="cb7d1-111">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="cb7d1-112">Use o <xref:System.Security.PermissionSet>classe para especificar o acesso a um membro.</xref:System.Security.PermissionSet></span><span class="sxs-lookup"><span data-stu-id="cb7d1-112">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="cb7d1-113">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="cb7d1-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb7d1-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cb7d1-114">Example</span></span>  
 <span data-ttu-id="cb7d1-115">Este exemplo usa o `<permission>` marca para descrever o que o <xref:System.Security.Permissions.FileIOPermission>é necessária para o `ReadFile` método.</xref:System.Security.Permissions.FileIOPermission></span><span class="sxs-lookup"><span data-stu-id="cb7d1-115">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 <span data-ttu-id="cb7d1-116">[!code-vb[VbVbcnXmlDocComments&#7;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="cb7d1-116">[!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb7d1-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb7d1-117">See Also</span></span>  
 [<span data-ttu-id="cb7d1-118">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="cb7d1-118">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
