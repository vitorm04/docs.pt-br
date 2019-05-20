---
title: Marcas recomendadas para comentários de documentação – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 963be5273389ebbdb3458d41b0658de0d94bb2cd
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634806"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>marcações recomendadas para comentários de documentação (Guia de Programação em C#)
O compilador do C# processa comentários de documentação em seu código e os formata como XML em um arquivo, cujo nome você especifica na opção de linha de comando **/doc**. Para criar a documentação final com base no arquivo gerado pelo compilador, crie uma ferramenta personalizada ou use uma ferramenta como o [DocFX](https://dotnet.github.io/docfx/) ou o [Sandcastle](https://github.com/EWSoftware/SHFB).  
  
 As marcas são processadas em constructos de código, como tipos e membros de tipo.  
  
> [!NOTE]
>  Os comentários de documentação não podem ser aplicados a um namespace.  
  
 O compilador processará qualquer marca que seja um XML válido. As seguintes marcas fornecem as funcionalidades geralmente usadas na documentação do usuário.  
  
## <a name="tags"></a>Marcas  
  
||||  
|---|---|---|  
|[\<c>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[\<para>](../../../csharp/programming-guide/xmldoc/para.md)|[\<see>](../../../csharp/programming-guide/xmldoc/see.md)*|  
|[\<code>](../../../csharp/programming-guide/xmldoc/code.md)|[\<param>](../../../csharp/programming-guide/xmldoc/param.md)*|[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)*|  
|[\<example>](../../../csharp/programming-guide/xmldoc/example.md)|[\<paramref>](../../../csharp/programming-guide/xmldoc/paramref.md)|[\<summary>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)*|[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)*|[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)*|  
|[\<include>](../../../csharp/programming-guide/xmldoc/include.md)*|[\<remarks>](../../../csharp/programming-guide/xmldoc/remarks.md)|[\<typeparamref>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[\<list>](../../../csharp/programming-guide/xmldoc/list.md)|[\<returns>](../../../csharp/programming-guide/xmldoc/returns.md)|[\<value>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 (* indica que o compilador verifica a sintaxe).  
  
 Se você quiser que os colchetes angulares sejam exibidos no texto de um comentário de documentação, use `<` e `>`, conforme mostrado no exemplo a seguir.  
  
```csharp  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [-doc (opções do compilador do C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [Comentários da documentação XML](../../../csharp/programming-guide/xmldoc/index.md)
