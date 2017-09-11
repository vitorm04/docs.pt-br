---
title: "&lt;permission&gt; (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- permission
- <permission>
dev_langs:
- CSharp
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4b8f109d7e01f6e630f09939161b6a20c3a13f73
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="ltpermissiongt-c-programming-guide"></a><span data-ttu-id="2c780-102">&lt;permission&gt; (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="2c780-102">&lt;permission&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="2c780-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2c780-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c780-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c780-104">Parameters</span></span>  
 <span data-ttu-id="2c780-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="2c780-105">cref = " `member`"</span></span>  
 <span data-ttu-id="2c780-106">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="2c780-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="2c780-107">O compilador verifica se o elemento de código fornecido existe e converte `member` no nome de elemento canônico no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="2c780-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="2c780-108">*member* deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="2c780-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="2c780-109">Para obter informações sobre como criar uma referência cref para um tipo genérico, consulte [ \<consulte>](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="2c780-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="2c780-110">Uma descrição do acesso ao membro.</span><span class="sxs-lookup"><span data-stu-id="2c780-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c780-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2c780-111">Remarks</span></span>  
 <span data-ttu-id="2c780-112">A marca \<permissão > permite documentar o acesso de um membro.</span><span class="sxs-lookup"><span data-stu-id="2c780-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="2c780-113">A classe <xref:System.Security.PermissionSet> permite que você especifique o acesso a um membro.</span><span class="sxs-lookup"><span data-stu-id="2c780-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="2c780-114">Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="2c780-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c780-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2c780-115">Example</span></span>  
 <span data-ttu-id="2c780-116">[!code-cs[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2c780-116">[!code-cs[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c780-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c780-117">See Also</span></span>  
 <span data-ttu-id="2c780-118">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2c780-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="2c780-119">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="2c780-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

