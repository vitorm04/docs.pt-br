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
ms.openlocfilehash: 9f877ee3fc9d616dc1e946293489a8aab96ac2e1
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872796"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="efc73-102">marcações XML recomendadas para comentários da documentação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efc73-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>

<span data-ttu-id="efc73-103">O compilador Visual Basic pode processar comentários de documentação em seu código para um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="efc73-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="efc73-104">Você pode usar ferramentas adicionais para processar o arquivo XML na documentação do.</span><span class="sxs-lookup"><span data-stu-id="efc73-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="efc73-105">Comentários XML são permitidos em construções de código, como tipos e membros de tipo.</span><span class="sxs-lookup"><span data-stu-id="efc73-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="efc73-106">Para tipos parciais, apenas uma parte do tipo pode ter comentários XML, embora não haja nenhuma restrição ao comentar seus membros.</span><span class="sxs-lookup"><span data-stu-id="efc73-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="efc73-107">Comentários de documentação não podem ser aplicados a namespaces.</span><span class="sxs-lookup"><span data-stu-id="efc73-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="efc73-108">O motivo é que um namespace pode abranger vários assemblies, e nem todos os assemblies precisam ser carregados ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="efc73-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="efc73-109">O compilador processa qualquer marca que seja XML válida.</span><span class="sxs-lookup"><span data-stu-id="efc73-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="efc73-110">As marcas a seguir fornecem funcionalidade comumente usada na documentação do usuário.</span><span class="sxs-lookup"><span data-stu-id="efc73-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[\<c>](c.md)|[\<code>](code.md)|[\<example>](example.md)|  
|<span data-ttu-id="efc73-111">[\<exception>](exception.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="efc73-111">[\<exception>](exception.md) <sup>1</sup></span></span>|<span data-ttu-id="efc73-112">[\<include>](include.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="efc73-112">[\<include>](include.md) <sup>1</sup></span></span>|[\<list>](list.md)|  
|[\<para>](para.md)|<span data-ttu-id="efc73-113">[\<param>](param.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="efc73-113">[\<param>](param.md) <sup>1</sup></span></span>|[\<paramref>](paramref.md)|  
|<span data-ttu-id="efc73-114">[\<permission>](permission.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="efc73-114">[\<permission>](permission.md) <sup>1</sup></span></span>|[\<remarks>](remarks.md)|[\<returns>](returns.md)|  
|<span data-ttu-id="efc73-115">[\<see>](see.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="efc73-115">[\<see>](see.md) <sup>1</sup></span></span>|<span data-ttu-id="efc73-116">[\<seealso>](seealso.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="efc73-116">[\<seealso>](seealso.md) <sup>1</sup></span></span>|[\<summary>](summary.md)|  
|<span data-ttu-id="efc73-117">[\<typeparam>](typeparam.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="efc73-117">[\<typeparam>](typeparam.md) <sup>1</sup></span></span>|[\<value>](value.md)||  
  
 <span data-ttu-id="efc73-118">(<sup>1</sup> o compilador verifica a sintaxe.)</span><span class="sxs-lookup"><span data-stu-id="efc73-118">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="efc73-119">Se você quiser que os colchetes angulares apareçam no texto de um comentário de documentação, use `&lt;` e `&gt;` .</span><span class="sxs-lookup"><span data-stu-id="efc73-119">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="efc73-120">Por exemplo, a cadeia de caracteres `"&lt;text in angle brackets&gt;"` será exibida como `<text in angle brackets>` .</span><span class="sxs-lookup"><span data-stu-id="efc73-120">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efc73-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="efc73-121">See also</span></span>

- [<span data-ttu-id="efc73-122">Documentando o código com XML</span><span class="sxs-lookup"><span data-stu-id="efc73-122">Documenting Your Code with XML</span></span>](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="efc73-123">-Doc</span><span class="sxs-lookup"><span data-stu-id="efc73-123">-doc</span></span>](../../reference/command-line-compiler/doc.md)
- [<span data-ttu-id="efc73-124">Como criar documentação XML</span><span class="sxs-lookup"><span data-stu-id="efc73-124">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
