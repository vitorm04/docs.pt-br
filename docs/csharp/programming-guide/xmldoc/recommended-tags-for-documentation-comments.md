---
title: Tags recomendadas para comentários de documentação - C# guia de programação
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789719"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="8764e-102">Tags recomendadas para comentários de documentação (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="8764e-102">Recommended tags for documentation comments (C# programming guide)</span></span>

<span data-ttu-id="8764e-103">O compilador do C# processa comentários de documentação em seu código e os formata como XML em um arquivo, cujo nome você especifica na opção de linha de comando **/doc**.</span><span class="sxs-lookup"><span data-stu-id="8764e-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="8764e-104">Para criar a documentação final com base no arquivo gerado pelo compilador, você pode criar uma ferramenta personalizada ou usar uma ferramenta como [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="8764e-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="8764e-105">As marcas são processadas em constructos de código, como tipos e membros de tipo.</span><span class="sxs-lookup"><span data-stu-id="8764e-105">Tags are processed on code constructs such as types and type members.</span></span>

> [!NOTE]
> <span data-ttu-id="8764e-106">Os comentários de documentação não podem ser aplicados a um namespace.</span><span class="sxs-lookup"><span data-stu-id="8764e-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="8764e-107">O compilador processará qualquer marca que seja um XML válido.</span><span class="sxs-lookup"><span data-stu-id="8764e-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="8764e-108">As seguintes marcas fornecem as funcionalidades geralmente usadas na documentação do usuário.</span><span class="sxs-lookup"><span data-stu-id="8764e-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="8764e-109">Marcas</span><span class="sxs-lookup"><span data-stu-id="8764e-109">Tags</span></span>  
  
|||||  
|---|---|---|---|
|[<span data-ttu-id="8764e-110">\<c></span><span class="sxs-lookup"><span data-stu-id="8764e-110">\<c></span></span>](./code-inline.md)|[<span data-ttu-id="8764e-111">\<para></span><span class="sxs-lookup"><span data-stu-id="8764e-111">\<para></span></span>](./para.md)|<span data-ttu-id="8764e-112">[\<ver>](./see.md)\*</span><span class="sxs-lookup"><span data-stu-id="8764e-112">[\<see>](./see.md)\*</span></span>|[<span data-ttu-id="8764e-113">\<>de valores</span><span class="sxs-lookup"><span data-stu-id="8764e-113">\<value></span></span>](./value.md)  
|[<span data-ttu-id="8764e-114">\<código></span><span class="sxs-lookup"><span data-stu-id="8764e-114">\<code></span></span>](./code.md)|<span data-ttu-id="8764e-115">[\<param>](./param.md)\*</span><span class="sxs-lookup"><span data-stu-id="8764e-115">[\<param>](./param.md)\*</span></span>|<span data-ttu-id="8764e-116">[\<vejatambém>](./seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="8764e-116">[\<seealso>](./seealso.md)\*</span></span>|  
|[<span data-ttu-id="8764e-117">\<exemplo></span><span class="sxs-lookup"><span data-stu-id="8764e-117">\<example></span></span>](./example.md)|[<span data-ttu-id="8764e-118">\<>paramref</span><span class="sxs-lookup"><span data-stu-id="8764e-118">\<paramref></span></span>](./paramref.md)|[<span data-ttu-id="8764e-119">\<>de resumo</span><span class="sxs-lookup"><span data-stu-id="8764e-119">\<summary></span></span>](./summary.md)|  
|<span data-ttu-id="8764e-120">[\<>exceção](./exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="8764e-120">[\<exception>](./exception.md)\*</span></span>|<span data-ttu-id="8764e-121">[\<permissão>](./permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="8764e-121">[\<permission>](./permission.md)\*</span></span>|<span data-ttu-id="8764e-122">[\<>de typeparam](./typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="8764e-122">[\<typeparam>](./typeparam.md)\*</span></span>|  
|<span data-ttu-id="8764e-123">[\<incluem>](./include.md)\*</span><span class="sxs-lookup"><span data-stu-id="8764e-123">[\<include>](./include.md)\*</span></span>|[<span data-ttu-id="8764e-124">\<observações></span><span class="sxs-lookup"><span data-stu-id="8764e-124">\<remarks></span></span>](./remarks.md)|[<span data-ttu-id="8764e-125">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="8764e-125">\<typeparamref></span></span>](./typeparamref.md)|  
|[<span data-ttu-id="8764e-126">\<lista></span><span class="sxs-lookup"><span data-stu-id="8764e-126">\<list></span></span>](./list.md)|[<span data-ttu-id="8764e-127">\<herdar></span><span class="sxs-lookup"><span data-stu-id="8764e-127">\<inheritdoc></span></span>](./inheritdoc.md)|[<span data-ttu-id="8764e-128">\<retorna></span><span class="sxs-lookup"><span data-stu-id="8764e-128">\<returns></span></span>](./returns.md)|
  
<span data-ttu-id="8764e-129">(denota\* que o compilador verifica a sintaxe.)</span><span class="sxs-lookup"><span data-stu-id="8764e-129">(\* denotes that the compiler verifies syntax.)</span></span>

<span data-ttu-id="8764e-130">Se você quiser que os colchetes angulares sejam exibidos no texto de um comentário de documentação, use a codificação HTML de `<` e `>`, que são `&lt;` e `&gt;` respectivamente.</span><span class="sxs-lookup"><span data-stu-id="8764e-130">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="8764e-131">Esta codificação é mostrada no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8764e-131">This encoding is shown in the following example.</span></span>

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a><span data-ttu-id="8764e-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="8764e-132">See also</span></span>

- [<span data-ttu-id="8764e-133">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="8764e-133">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="8764e-134">-doc (opções de compilador C#)</span><span class="sxs-lookup"><span data-stu-id="8764e-134">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="8764e-135">Comentários da documentação XML</span><span class="sxs-lookup"><span data-stu-id="8764e-135">XML documentation comments</span></span>](./index.md)
