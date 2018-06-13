---
title: '&lt;permission&gt; (Guia de Programação em C#)'
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 815d303c9cfbf01588f5f2877e9f87a7ebbea9a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321471"
---
# <a name="ltpermissiongt-c-programming-guide"></a><span data-ttu-id="90db4-102">&lt;permission&gt; (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="90db4-102">&lt;permission&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="90db4-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90db4-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90db4-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="90db4-104">Parameters</span></span>  
 <span data-ttu-id="90db4-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="90db4-105">cref = " `member`"</span></span>  
 <span data-ttu-id="90db4-106">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="90db4-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="90db4-107">O compilador verifica se o elemento de código fornecido existe e converte `member` no nome de elemento canônico no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="90db4-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="90db4-108">*member* deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="90db4-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="90db4-109">Para obter informações sobre como criar uma referência cref para um tipo genérico, consulte [ \<consulte>](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="90db4-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="90db4-110">Uma descrição do acesso ao membro.</span><span class="sxs-lookup"><span data-stu-id="90db4-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90db4-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="90db4-111">Remarks</span></span>  
 <span data-ttu-id="90db4-112">A marca \<permissão > permite documentar o acesso de um membro.</span><span class="sxs-lookup"><span data-stu-id="90db4-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="90db4-113">A classe <xref:System.Security.PermissionSet> permite que você especifique o acesso a um membro.</span><span class="sxs-lookup"><span data-stu-id="90db4-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="90db4-114">Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="90db4-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90db4-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="90db4-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="90db4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90db4-116">See Also</span></span>  
 [<span data-ttu-id="90db4-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="90db4-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="90db4-118">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="90db4-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
