---
title: "Marcas XML recomendadas para comentários da documentação (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlDocComment
dev_langs:
- VB
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: 14
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e4a6c3128a69e8d666d44882ef3eac9f9a31a51a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="59bf0-102">marcações XML recomendadas para comentários da documentação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59bf0-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="59bf0-103">O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador pode processar comentários de documentação em seu código para um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="59bf0-103">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="59bf0-104">Você pode usar ferramentas adicionais para processar o arquivo XML em documentação.</span><span class="sxs-lookup"><span data-stu-id="59bf0-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="59bf0-105">Comentários XML são permitidos em construções de código, como tipos e membros de tipo.</span><span class="sxs-lookup"><span data-stu-id="59bf0-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="59bf0-106">Para tipos parciais, apenas uma parte do tipo pode ter comentários XML, embora não haja nenhuma restrição em comentar seus membros.</span><span class="sxs-lookup"><span data-stu-id="59bf0-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59bf0-107">Comentários de documentação não podem ser aplicados a namespaces.</span><span class="sxs-lookup"><span data-stu-id="59bf0-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="59bf0-108">O motivo é que um namespace pode abranger vários assemblies, e não todos os assemblies tenham que ser carregados ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="59bf0-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="59bf0-109">O compilador processa qualquer marca que é XML válido.</span><span class="sxs-lookup"><span data-stu-id="59bf0-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="59bf0-110">As seguintes marcas fornecem funcionalidades comumente usadas na documentação do usuário.</span><span class="sxs-lookup"><span data-stu-id="59bf0-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="59bf0-111">\<c ></span><span class="sxs-lookup"><span data-stu-id="59bf0-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="59bf0-112">\<código ></span><span class="sxs-lookup"><span data-stu-id="59bf0-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="59bf0-113">\<exemplo ></span><span class="sxs-lookup"><span data-stu-id="59bf0-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="59bf0-114">[\<exceção >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="59bf0-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="59bf0-115">[\<incluir >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="59bf0-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="59bf0-116">\<list></span><span class="sxs-lookup"><span data-stu-id="59bf0-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="59bf0-117">\<para ></span><span class="sxs-lookup"><span data-stu-id="59bf0-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="59bf0-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="59bf0-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="59bf0-119">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="59bf0-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="59bf0-120">[\<permissão >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="59bf0-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="59bf0-121">\<comentários ></span><span class="sxs-lookup"><span data-stu-id="59bf0-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="59bf0-122">\<Retorna ></span><span class="sxs-lookup"><span data-stu-id="59bf0-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="59bf0-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="59bf0-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="59bf0-124">[\<Consulte também >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="59bf0-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="59bf0-125">\<Resumo ></span><span class="sxs-lookup"><span data-stu-id="59bf0-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="59bf0-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="59bf0-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="59bf0-127">\<valor ></span><span class="sxs-lookup"><span data-stu-id="59bf0-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="59bf0-128">(<sup>1</sup> o compilador verifica a sintaxe.)</span><span class="sxs-lookup"><span data-stu-id="59bf0-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59bf0-129">Se você quiser que colchetes angulares sejam exibido no texto de um comentário de documentação, use `<` e `>`.</span><span class="sxs-lookup"><span data-stu-id="59bf0-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`.</span></span> <span data-ttu-id="59bf0-130">Por exemplo, a cadeia de caracteres `"<text in angle brackets>"` será exibido como `<text in angle``brackets>`.</span><span class="sxs-lookup"><span data-stu-id="59bf0-130">For example, the string `"<text in angle brackets>"` will appear as `<text in angle``brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59bf0-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59bf0-131">See Also</span></span>  
 <span data-ttu-id="59bf0-132">[Documentar seu código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) </span><span class="sxs-lookup"><span data-stu-id="59bf0-132">[Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) </span></span>  
<span data-ttu-id="59bf0-133"> [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) </span><span class="sxs-lookup"><span data-stu-id="59bf0-133"> [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) </span></span>  
<span data-ttu-id="59bf0-134"> [Como criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)</span><span class="sxs-lookup"><span data-stu-id="59bf0-134"> [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)</span></span>
