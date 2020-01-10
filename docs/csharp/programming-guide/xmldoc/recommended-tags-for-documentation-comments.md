---
title: Marcas recomendadas para comentários de documentação – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 15a183d72a7d3e47f99227cea2cf870ad2f98d18
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75696526"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="efcd2-102">marcações recomendadas para comentários de documentação (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="efcd2-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="efcd2-103">O compilador do C# processa comentários de documentação em seu código e os formata como XML em um arquivo, cujo nome você especifica na opção de linha de comando **/doc**.</span><span class="sxs-lookup"><span data-stu-id="efcd2-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="efcd2-104">Para criar a documentação final com base no arquivo gerado pelo compilador, crie uma ferramenta personalizada ou use uma ferramenta como o [DocFX](https://dotnet.github.io/docfx/) ou o [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="efcd2-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="efcd2-105">As marcas são processadas em constructos de código, como tipos e membros de tipo.</span><span class="sxs-lookup"><span data-stu-id="efcd2-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="efcd2-106">Os comentários de documentação não podem ser aplicados a um namespace.</span><span class="sxs-lookup"><span data-stu-id="efcd2-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="efcd2-107">O compilador processará qualquer marca que seja um XML válido.</span><span class="sxs-lookup"><span data-stu-id="efcd2-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="efcd2-108">As seguintes marcas fornecem as funcionalidades geralmente usadas na documentação do usuário.</span><span class="sxs-lookup"><span data-stu-id="efcd2-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="efcd2-109">Marcas</span><span class="sxs-lookup"><span data-stu-id="efcd2-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="efcd2-110">\<c></span><span class="sxs-lookup"><span data-stu-id="efcd2-110">\<c></span></span>](./code-inline.md)|[<span data-ttu-id="efcd2-111">\<para></span><span class="sxs-lookup"><span data-stu-id="efcd2-111">\<para></span></span>](./para.md)|<span data-ttu-id="efcd2-112">[\<see>](./see.md)\*</span><span class="sxs-lookup"><span data-stu-id="efcd2-112">[\<see>](./see.md)\*</span></span>|  
|[<span data-ttu-id="efcd2-113">\<code></span><span class="sxs-lookup"><span data-stu-id="efcd2-113">\<code></span></span>](./code.md)|<span data-ttu-id="efcd2-114">[\<param>](./param.md)\*</span><span class="sxs-lookup"><span data-stu-id="efcd2-114">[\<param>](./param.md)\*</span></span>|<span data-ttu-id="efcd2-115">[\<seealso>](./seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="efcd2-115">[\<seealso>](./seealso.md)\*</span></span>|  
|[<span data-ttu-id="efcd2-116">\<example></span><span class="sxs-lookup"><span data-stu-id="efcd2-116">\<example></span></span>](./example.md)|[<span data-ttu-id="efcd2-117">\<paramref></span><span class="sxs-lookup"><span data-stu-id="efcd2-117">\<paramref></span></span>](./paramref.md)|[<span data-ttu-id="efcd2-118">\<summary></span><span class="sxs-lookup"><span data-stu-id="efcd2-118">\<summary></span></span>](./summary.md)|  
|<span data-ttu-id="efcd2-119">[\<exception>](./exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="efcd2-119">[\<exception>](./exception.md)\*</span></span>|<span data-ttu-id="efcd2-120">[\<permission>](./permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="efcd2-120">[\<permission>](./permission.md)\*</span></span>|<span data-ttu-id="efcd2-121">[\<typeparam>](./typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="efcd2-121">[\<typeparam>](./typeparam.md)\*</span></span>|  
|<span data-ttu-id="efcd2-122">[\<include>](./include.md)\*</span><span class="sxs-lookup"><span data-stu-id="efcd2-122">[\<include>](./include.md)\*</span></span>|[<span data-ttu-id="efcd2-123">\<remarks></span><span class="sxs-lookup"><span data-stu-id="efcd2-123">\<remarks></span></span>](./remarks.md)|[<span data-ttu-id="efcd2-124">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="efcd2-124">\<typeparamref></span></span>](./typeparamref.md)|  
|[<span data-ttu-id="efcd2-125">\<list></span><span class="sxs-lookup"><span data-stu-id="efcd2-125">\<list></span></span>](./list.md)|[<span data-ttu-id="efcd2-126">\<returns></span><span class="sxs-lookup"><span data-stu-id="efcd2-126">\<returns></span></span>](./returns.md)|[<span data-ttu-id="efcd2-127">\<value></span><span class="sxs-lookup"><span data-stu-id="efcd2-127">\<value></span></span>](./value.md)|  
  
 <span data-ttu-id="efcd2-128">(\* indica que o compilador verifica a sintaxe).</span><span class="sxs-lookup"><span data-stu-id="efcd2-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="efcd2-129">Se você quiser que os colchetes angulares sejam exibidos no texto de um comentário de documentação, use a codificação HTML de `<` e `>`, que são `&lt;` e `&gt;` respectivamente.</span><span class="sxs-lookup"><span data-stu-id="efcd2-129">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="efcd2-130">Essa codificação é mostrada no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="efcd2-130">This encoding is shown in the following example:</span></span>
  
```csharp  
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```
  
## <a name="see-also"></a><span data-ttu-id="efcd2-131">Veja também</span><span class="sxs-lookup"><span data-stu-id="efcd2-131">See also</span></span>

- [<span data-ttu-id="efcd2-132">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="efcd2-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="efcd2-133">-doc (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="efcd2-133">-doc (C# Compiler Options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="efcd2-134">Comentários da documentação XML</span><span class="sxs-lookup"><span data-stu-id="efcd2-134">XML Documentation Comments</span></span>](./index.md)
