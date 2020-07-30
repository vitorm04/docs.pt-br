---
title: Marcas recomendadas para comentários de documentação – guia de programação C#
description: Saiba mais sobre as marcas recomendadas para comentários de documentação. Consulte uma lista de marcas recomendadas e exiba recursos adicionais disponíveis.
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 65bca6f979c5ffd91507b571a4f049377315192d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381509"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="34375-104">Marcas recomendadas para comentários de documentação (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="34375-104">Recommended tags for documentation comments (C# programming guide)</span></span>

<span data-ttu-id="34375-105">O compilador do C# processa comentários de documentação em seu código e os formata como XML em um arquivo, cujo nome você especifica na opção de linha de comando **/doc**.</span><span class="sxs-lookup"><span data-stu-id="34375-105">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="34375-106">Para criar a documentação final com base no arquivo gerado pelo compilador, você pode criar uma ferramenta personalizada ou usar uma ferramenta como [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="34375-106">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="34375-107">As marcas são processadas em constructos de código, como tipos e membros de tipo.</span><span class="sxs-lookup"><span data-stu-id="34375-107">Tags are processed on code constructs such as types and type members.</span></span>

> [!NOTE]
> <span data-ttu-id="34375-108">Os comentários de documentação não podem ser aplicados a um namespace.</span><span class="sxs-lookup"><span data-stu-id="34375-108">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="34375-109">O compilador processará qualquer marca que seja um XML válido.</span><span class="sxs-lookup"><span data-stu-id="34375-109">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="34375-110">As seguintes marcas fornecem as funcionalidades geralmente usadas na documentação do usuário.</span><span class="sxs-lookup"><span data-stu-id="34375-110">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="34375-111">Marcas</span><span class="sxs-lookup"><span data-stu-id="34375-111">Tags</span></span>  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<see>](./see.md)*|[\<value>](./value.md)  
|[\<code>](./code.md)|[\<param>](./param.md)*|[\<seealso>](./seealso.md)*|  
|[\<example>](./example.md)|[\<paramref>](./paramref.md)|[\<summary>](./summary.md)|  
|[\<exception>](./exception.md)*|[\<permission>](./permission.md)*|[\<typeparam>](./typeparam.md)*|  
|[\<include>](./include.md)*|[\<remarks>](./remarks.md)|[\<typeparamref>](./typeparamref.md)|  
|[\<list>](./list.md)|[\<inheritdoc>](./inheritdoc.md)|[\<returns>](./returns.md)|
  
<span data-ttu-id="34375-112">( \* indica que o compilador verifica a sintaxe.)</span><span class="sxs-lookup"><span data-stu-id="34375-112">(\* denotes that the compiler verifies syntax.)</span></span>

<span data-ttu-id="34375-113">Se você quiser que os colchetes angulares sejam exibidos no texto de um comentário de documentação, use a codificação HTML de `<` e `>`, que são `&lt;` e `&gt;` respectivamente.</span><span class="sxs-lookup"><span data-stu-id="34375-113">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="34375-114">Essa codificação é mostrada no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="34375-114">This encoding is shown in the following example.</span></span>

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a><span data-ttu-id="34375-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="34375-115">See also</span></span>

- [<span data-ttu-id="34375-116">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="34375-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="34375-117">-Doc (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="34375-117">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="34375-118">Comentários da documentação XML</span><span class="sxs-lookup"><span data-stu-id="34375-118">XML documentation comments</span></span>](./index.md)
