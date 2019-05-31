---
title: Marcas recomendadas para comentários de documentação – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 07594d70b92e2075c3d5aba605eab23d766faed6
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052742"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="fed11-102">marcações recomendadas para comentários de documentação (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="fed11-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="fed11-103">O compilador do C# processa comentários de documentação em seu código e os formata como XML em um arquivo, cujo nome você especifica na opção de linha de comando **/doc**.</span><span class="sxs-lookup"><span data-stu-id="fed11-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="fed11-104">Para criar a documentação final com base no arquivo gerado pelo compilador, crie uma ferramenta personalizada ou use uma ferramenta como o [DocFX](https://dotnet.github.io/docfx/) ou o [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="fed11-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="fed11-105">As marcas são processadas em constructos de código, como tipos e membros de tipo.</span><span class="sxs-lookup"><span data-stu-id="fed11-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fed11-106">Os comentários de documentação não podem ser aplicados a um namespace.</span><span class="sxs-lookup"><span data-stu-id="fed11-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="fed11-107">O compilador processará qualquer marca que seja um XML válido.</span><span class="sxs-lookup"><span data-stu-id="fed11-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="fed11-108">As seguintes marcas fornecem as funcionalidades geralmente usadas na documentação do usuário.</span><span class="sxs-lookup"><span data-stu-id="fed11-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="fed11-109">Marcas</span><span class="sxs-lookup"><span data-stu-id="fed11-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="fed11-110">\<c></span><span class="sxs-lookup"><span data-stu-id="fed11-110">\<c></span></span>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[<span data-ttu-id="fed11-111">\<para></span><span class="sxs-lookup"><span data-stu-id="fed11-111">\<para></span></span>](../../../csharp/programming-guide/xmldoc/para.md)|<span data-ttu-id="fed11-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)\*</span><span class="sxs-lookup"><span data-stu-id="fed11-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)\*</span></span>|  
|[<span data-ttu-id="fed11-113">\<code></span><span class="sxs-lookup"><span data-stu-id="fed11-113">\<code></span></span>](../../../csharp/programming-guide/xmldoc/code.md)|<span data-ttu-id="fed11-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)\*</span><span class="sxs-lookup"><span data-stu-id="fed11-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)\*</span></span>|<span data-ttu-id="fed11-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="fed11-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span></span>|  
|[<span data-ttu-id="fed11-116">\<example></span><span class="sxs-lookup"><span data-stu-id="fed11-116">\<example></span></span>](../../../csharp/programming-guide/xmldoc/example.md)|[<span data-ttu-id="fed11-117">\<paramref></span><span class="sxs-lookup"><span data-stu-id="fed11-117">\<paramref></span></span>](../../../csharp/programming-guide/xmldoc/paramref.md)|[<span data-ttu-id="fed11-118">\<summary></span><span class="sxs-lookup"><span data-stu-id="fed11-118">\<summary></span></span>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|<span data-ttu-id="fed11-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="fed11-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)\*</span></span>|<span data-ttu-id="fed11-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="fed11-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)\*</span></span>|<span data-ttu-id="fed11-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="fed11-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span></span>|  
|<span data-ttu-id="fed11-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)\*</span><span class="sxs-lookup"><span data-stu-id="fed11-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)\*</span></span>|[<span data-ttu-id="fed11-123">\<remarks></span><span class="sxs-lookup"><span data-stu-id="fed11-123">\<remarks></span></span>](../../../csharp/programming-guide/xmldoc/remarks.md)|[<span data-ttu-id="fed11-124">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="fed11-124">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[<span data-ttu-id="fed11-125">\<list></span><span class="sxs-lookup"><span data-stu-id="fed11-125">\<list></span></span>](../../../csharp/programming-guide/xmldoc/list.md)|[<span data-ttu-id="fed11-126">\<returns></span><span class="sxs-lookup"><span data-stu-id="fed11-126">\<returns></span></span>](../../../csharp/programming-guide/xmldoc/returns.md)|[<span data-ttu-id="fed11-127">\<value></span><span class="sxs-lookup"><span data-stu-id="fed11-127">\<value></span></span>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 <span data-ttu-id="fed11-128">(\* indica que o compilador verifica a sintaxe).</span><span class="sxs-lookup"><span data-stu-id="fed11-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="fed11-129">Se você quiser que os colchetes angulares sejam exibidos no texto de um comentário de documentação, use a codificação HTML de `<` e `>`, que são `&lt;` e `&gt;` respectivamente.</span><span class="sxs-lookup"><span data-stu-id="fed11-129">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="fed11-130">Essa codificação é mostrada no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="fed11-130">This encoding is shown in the following example:</span></span>
  
```csharp  
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```
  
## <a name="see-also"></a><span data-ttu-id="fed11-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fed11-131">See also</span></span>

- [<span data-ttu-id="fed11-132">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="fed11-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="fed11-133">-doc (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="fed11-133">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="fed11-134">Comentários da documentação XML</span><span class="sxs-lookup"><span data-stu-id="fed11-134">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/index.md)
