---
title: Marcas recomendadas para comentários de C# documentação – guia de programação
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789719"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Marcas recomendadas para comentários deC# documentação (guia de programação)

O compilador do C# processa comentários de documentação em seu código e os formata como XML em um arquivo, cujo nome você especifica na opção de linha de comando **/doc**. Para criar a documentação final com base no arquivo gerado pelo compilador, crie uma ferramenta personalizada ou use uma ferramenta como o [DocFX](https://dotnet.github.io/docfx/) ou o [Sandcastle](https://github.com/EWSoftware/SHFB).

As marcas são processadas em constructos de código, como tipos e membros de tipo.

> [!NOTE]
> Os comentários de documentação não podem ser aplicados a um namespace.  
  
 O compilador processará qualquer marca que seja um XML válido. As seguintes marcas fornecem as funcionalidades geralmente usadas na documentação do usuário.  
  
## <a name="tags"></a>Marcas  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<see>](./see.md)*|[\<value>](./value.md)  
|[\<code>](./code.md)|[\<param>](./param.md)*|[\<seealso>](./seealso.md)*|  
|[\<example>](./example.md)|[\<paramref>](./paramref.md)|[\<summary>](./summary.md)|  
|[\<exception>](./exception.md)*|[\<permission>](./permission.md)*|[\<typeparam>](./typeparam.md)*|  
|[\<include>](./include.md)*|[\<remarks>](./remarks.md)|[\<typeparamref>](./typeparamref.md)|  
|[\<list>](./list.md)|[\<inheritdoc >](./inheritdoc.md)|[\<returns>](./returns.md)|
  
(\* indica que o compilador verifica a sintaxe.)

Se você quiser que os colchetes angulares sejam exibidos no texto de um comentário de documentação, use a codificação HTML de `<` e `>`, que são `&lt;` e `&gt;` respectivamente. Essa codificação é mostrada no exemplo a seguir.

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a>Veja também

- [Guia de programação em C#](../index.md)
- [-Doc (C# opções do compilador)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Comentários de documentação XML](./index.md)
