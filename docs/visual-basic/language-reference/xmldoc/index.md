---
title: Marcas XML recomendadas para comentários de documentação
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: af57fc7d55c5cfda24a2fd9406b17dedee898760
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400093"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="55eff-102">marcações XML recomendadas para comentários da documentação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55eff-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="55eff-103">O compilador Visual Basic pode processar comentários de documentação em seu código para um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="55eff-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="55eff-104">Você pode usar ferramentas adicionais para processar o arquivo XML na documentação do.</span><span class="sxs-lookup"><span data-stu-id="55eff-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="55eff-105">Comentários XML são permitidos em construções de código, como tipos e membros de tipo.</span><span class="sxs-lookup"><span data-stu-id="55eff-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="55eff-106">Para tipos parciais, apenas uma parte do tipo pode ter comentários XML, embora não haja nenhuma restrição ao comentar seus membros.</span><span class="sxs-lookup"><span data-stu-id="55eff-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55eff-107">Comentários de documentação não podem ser aplicados a namespaces.</span><span class="sxs-lookup"><span data-stu-id="55eff-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="55eff-108">O motivo é que um namespace pode abranger vários assemblies, e nem todos os assemblies precisam ser carregados ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="55eff-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="55eff-109">O compilador processa qualquer marca que seja XML válida.</span><span class="sxs-lookup"><span data-stu-id="55eff-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="55eff-110">As marcas a seguir fornecem funcionalidade comumente usada na documentação do usuário.</span><span class="sxs-lookup"><span data-stu-id="55eff-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[\<c>](c.md)|[\<code>](code.md)|[\<example>](example.md)|  
|<span data-ttu-id="55eff-111">[\<exception>](exception.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="55eff-111">[\<exception>](exception.md) <sup>1</sup></span></span>|<span data-ttu-id="55eff-112">[\<include>](include.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="55eff-112">[\<include>](include.md) <sup>1</sup></span></span>|[\<list>](list.md)|  
|[\<para>](para.md)|<span data-ttu-id="55eff-113">[\<param>](param.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="55eff-113">[\<param>](param.md) <sup>1</sup></span></span>|[\<paramref>](paramref.md)|  
|<span data-ttu-id="55eff-114">[\<permission>](permission.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="55eff-114">[\<permission>](permission.md) <sup>1</sup></span></span>|[\<remarks>](remarks.md)|[\<returns>](returns.md)|  
|<span data-ttu-id="55eff-115">[\<see>](see.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="55eff-115">[\<see>](see.md) <sup>1</sup></span></span>|<span data-ttu-id="55eff-116">[\<seealso>](seealso.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="55eff-116">[\<seealso>](seealso.md) <sup>1</sup></span></span>|[\<summary>](summary.md)|  
|<span data-ttu-id="55eff-117">[\<typeparam>](typeparam.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="55eff-117">[\<typeparam>](typeparam.md) <sup>1</sup></span></span>|[\<value>](value.md)||  
  
 <span data-ttu-id="55eff-118">(<sup>1</sup> o compilador verifica a sintaxe.)</span><span class="sxs-lookup"><span data-stu-id="55eff-118">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55eff-119">Se você quiser que os colchetes angulares apareçam no texto de um comentário de documentação, use `&lt;` e `&gt;` .</span><span class="sxs-lookup"><span data-stu-id="55eff-119">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="55eff-120">Por exemplo, a cadeia de caracteres `"&lt;text in angle brackets&gt;"` será exibida como `<text in angle brackets>` .</span><span class="sxs-lookup"><span data-stu-id="55eff-120">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55eff-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="55eff-121">See also</span></span>

- [<span data-ttu-id="55eff-122">Documentando o código com XML</span><span class="sxs-lookup"><span data-stu-id="55eff-122">Documenting Your Code with XML</span></span>](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="55eff-123">-doc</span><span class="sxs-lookup"><span data-stu-id="55eff-123">-doc</span></span>](../../reference/command-line-compiler/doc.md)
- [<span data-ttu-id="55eff-124">Como criar documentação XML</span><span class="sxs-lookup"><span data-stu-id="55eff-124">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
