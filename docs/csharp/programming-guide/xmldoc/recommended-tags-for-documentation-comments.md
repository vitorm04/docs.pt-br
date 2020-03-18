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
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Tags recomendadas para comentários de documentação (guia de programação C#)

O compilador do C# processa comentários de documentação em seu código e os formata como XML em um arquivo, cujo nome você especifica na opção de linha de comando **/doc**. Para criar a documentação final com base no arquivo gerado pelo compilador, você pode criar uma ferramenta personalizada ou usar uma ferramenta como [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB).

As marcas são processadas em constructos de código, como tipos e membros de tipo.

> [!NOTE]
> Os comentários de documentação não podem ser aplicados a um namespace.  
  
 O compilador processará qualquer marca que seja um XML válido. As seguintes marcas fornecem as funcionalidades geralmente usadas na documentação do usuário.  
  
## <a name="tags"></a>Marcas  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<ver>](./see.md)*|[\<>de valores](./value.md)  
|[\<código>](./code.md)|[\<param>](./param.md)*|[\<vejatambém>](./seealso.md)*|  
|[\<exemplo>](./example.md)|[\<>paramref](./paramref.md)|[\<>de resumo](./summary.md)|  
|[\<>exceção](./exception.md)*|[\<permissão>](./permission.md)*|[\<>de typeparam](./typeparam.md)*|  
|[\<incluem>](./include.md)*|[\<observações>](./remarks.md)|[\<typeparamref>](./typeparamref.md)|  
|[\<lista>](./list.md)|[\<herdar>](./inheritdoc.md)|[\<retorna>](./returns.md)|
  
(denota\* que o compilador verifica a sintaxe.)

Se você quiser que os colchetes angulares sejam exibidos no texto de um comentário de documentação, use a codificação HTML de `<` e `>`, que são `&lt;` e `&gt;` respectivamente. Esta codificação é mostrada no exemplo a seguir.

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a>Confira também

- [Guia de programação em C#](../index.md)
- [-doc (opções de compilador C#)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Comentários da documentação XML](./index.md)
