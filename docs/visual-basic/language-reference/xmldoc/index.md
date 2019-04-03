---
title: marcações XML recomendadas para comentários da documentação (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: e59ee25b22c51e47dc83233af33099e6c55de87b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814933"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="e84ec-102">marcações XML recomendadas para comentários da documentação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e84ec-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="e84ec-103">O compilador do Visual Basic pode processar comentários de documentação em seu código para um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="e84ec-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="e84ec-104">Você pode usar ferramentas adicionais para processar o arquivo XML em documentação.</span><span class="sxs-lookup"><span data-stu-id="e84ec-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="e84ec-105">Comentários XML são permitidos em construções de código, como tipos e membros de tipo.</span><span class="sxs-lookup"><span data-stu-id="e84ec-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="e84ec-106">Para tipos parciais, apenas uma parte do tipo pode ter comentários XML, embora não haja nenhuma restrição em comentar seus membros.</span><span class="sxs-lookup"><span data-stu-id="e84ec-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e84ec-107">Comentários de documentação não podem ser aplicados a namespaces.</span><span class="sxs-lookup"><span data-stu-id="e84ec-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="e84ec-108">O motivo é que um namespace pode abranger vários assemblies, e nem todos os assemblies precisam ser carregados ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="e84ec-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="e84ec-109">O compilador processa qualquer marca que é um XML válido.</span><span class="sxs-lookup"><span data-stu-id="e84ec-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="e84ec-110">As seguintes marcas fornecem funcionalidades comumente usadas na documentação do usuário.</span><span class="sxs-lookup"><span data-stu-id="e84ec-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="e84ec-111">\<c></span><span class="sxs-lookup"><span data-stu-id="e84ec-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="e84ec-112">\<code></span><span class="sxs-lookup"><span data-stu-id="e84ec-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="e84ec-113">\<example></span><span class="sxs-lookup"><span data-stu-id="e84ec-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="e84ec-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e84ec-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="e84ec-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e84ec-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="e84ec-116">\<list></span><span class="sxs-lookup"><span data-stu-id="e84ec-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="e84ec-117">\<para></span><span class="sxs-lookup"><span data-stu-id="e84ec-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="e84ec-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e84ec-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="e84ec-119">\<paramref></span><span class="sxs-lookup"><span data-stu-id="e84ec-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="e84ec-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e84ec-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="e84ec-121">\<remarks></span><span class="sxs-lookup"><span data-stu-id="e84ec-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="e84ec-122">\<returns></span><span class="sxs-lookup"><span data-stu-id="e84ec-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="e84ec-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e84ec-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="e84ec-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e84ec-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="e84ec-125">\<summary></span><span class="sxs-lookup"><span data-stu-id="e84ec-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="e84ec-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e84ec-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="e84ec-127">\<value></span><span class="sxs-lookup"><span data-stu-id="e84ec-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="e84ec-128">(<sup>1</sup> o compilador verifica a sintaxe.)</span><span class="sxs-lookup"><span data-stu-id="e84ec-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e84ec-129">Se você quiser colchetes angulares sejam exibidos no texto de um comentário de documentação, use `&lt;` e `&gt;`.</span><span class="sxs-lookup"><span data-stu-id="e84ec-129">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="e84ec-130">Por exemplo, a cadeia de caracteres `"&lt;text in angle brackets&gt;"` será exibido como `<text in angle brackets>`.</span><span class="sxs-lookup"><span data-stu-id="e84ec-130">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e84ec-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e84ec-131">See also</span></span>

- [<span data-ttu-id="e84ec-132">Documentando o Código com XML</span><span class="sxs-lookup"><span data-stu-id="e84ec-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="e84ec-133">/doc</span><span class="sxs-lookup"><span data-stu-id="e84ec-133">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
- [<span data-ttu-id="e84ec-134">Como: Criar documentação XML</span><span class="sxs-lookup"><span data-stu-id="e84ec-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
