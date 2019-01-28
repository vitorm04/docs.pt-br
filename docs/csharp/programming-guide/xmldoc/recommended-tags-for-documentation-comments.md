---
title: Marcas recomendadas para comentários de documentação – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: bdebe26c89f3c7e8d34d34f305d658cd481cd677
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723427"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="3daf9-102">marcações recomendadas para comentários de documentação (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="3daf9-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="3daf9-103">O compilador do C# processa comentários de documentação em seu código e os formata como XML em um arquivo, cujo nome você especifica na opção de linha de comando **/doc**.</span><span class="sxs-lookup"><span data-stu-id="3daf9-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="3daf9-104">Para criar a documentação final baseada no arquivo gerado pelo compilador, você pode criar uma ferramenta personalizada ou usar uma ferramenta como o [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="3daf9-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="3daf9-105">As marcas são processadas em constructos de código, como tipos e membros de tipo.</span><span class="sxs-lookup"><span data-stu-id="3daf9-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3daf9-106">Os comentários de documentação não podem ser aplicados a um namespace.</span><span class="sxs-lookup"><span data-stu-id="3daf9-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="3daf9-107">O compilador processará qualquer marca que seja um XML válido.</span><span class="sxs-lookup"><span data-stu-id="3daf9-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="3daf9-108">As seguintes marcas fornecem as funcionalidades geralmente usadas na documentação do usuário.</span><span class="sxs-lookup"><span data-stu-id="3daf9-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="3daf9-109">Marcas</span><span class="sxs-lookup"><span data-stu-id="3daf9-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="3daf9-110">\<c></span><span class="sxs-lookup"><span data-stu-id="3daf9-110">\<c></span></span>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[<span data-ttu-id="3daf9-111">\<para></span><span class="sxs-lookup"><span data-stu-id="3daf9-111">\<para></span></span>](../../../csharp/programming-guide/xmldoc/para.md)|<span data-ttu-id="3daf9-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)\*</span><span class="sxs-lookup"><span data-stu-id="3daf9-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)\*</span></span>|  
|[<span data-ttu-id="3daf9-113">\<code></span><span class="sxs-lookup"><span data-stu-id="3daf9-113">\<code></span></span>](../../../csharp/programming-guide/xmldoc/code.md)|<span data-ttu-id="3daf9-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)\*</span><span class="sxs-lookup"><span data-stu-id="3daf9-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)\*</span></span>|<span data-ttu-id="3daf9-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="3daf9-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span></span>|  
|[<span data-ttu-id="3daf9-116">\<example></span><span class="sxs-lookup"><span data-stu-id="3daf9-116">\<example></span></span>](../../../csharp/programming-guide/xmldoc/example.md)|[<span data-ttu-id="3daf9-117">\<paramref></span><span class="sxs-lookup"><span data-stu-id="3daf9-117">\<paramref></span></span>](../../../csharp/programming-guide/xmldoc/paramref.md)|[<span data-ttu-id="3daf9-118">\<summary></span><span class="sxs-lookup"><span data-stu-id="3daf9-118">\<summary></span></span>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|<span data-ttu-id="3daf9-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="3daf9-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)\*</span></span>|<span data-ttu-id="3daf9-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="3daf9-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)\*</span></span>|<span data-ttu-id="3daf9-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="3daf9-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span></span>|  
|<span data-ttu-id="3daf9-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)\*</span><span class="sxs-lookup"><span data-stu-id="3daf9-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)\*</span></span>|[<span data-ttu-id="3daf9-123">\<remarks></span><span class="sxs-lookup"><span data-stu-id="3daf9-123">\<remarks></span></span>](../../../csharp/programming-guide/xmldoc/remarks.md)|[<span data-ttu-id="3daf9-124">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="3daf9-124">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[<span data-ttu-id="3daf9-125">\<list></span><span class="sxs-lookup"><span data-stu-id="3daf9-125">\<list></span></span>](../../../csharp/programming-guide/xmldoc/list.md)|[<span data-ttu-id="3daf9-126">\<returns></span><span class="sxs-lookup"><span data-stu-id="3daf9-126">\<returns></span></span>](../../../csharp/programming-guide/xmldoc/returns.md)|[<span data-ttu-id="3daf9-127">\<value></span><span class="sxs-lookup"><span data-stu-id="3daf9-127">\<value></span></span>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 <span data-ttu-id="3daf9-128">(\* indica que o compilador verifica a sintaxe).</span><span class="sxs-lookup"><span data-stu-id="3daf9-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="3daf9-129">Se você quiser que os colchetes angulares sejam exibidos no texto de um comentário de documentação, use `<` e `>`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3daf9-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`, as shown in the following example.</span></span>  
  
```csharp  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3daf9-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3daf9-130">See also</span></span>

- [<span data-ttu-id="3daf9-131">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3daf9-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3daf9-132">-doc (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="3daf9-132">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="3daf9-133">Comentários da documentação XML</span><span class="sxs-lookup"><span data-stu-id="3daf9-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
