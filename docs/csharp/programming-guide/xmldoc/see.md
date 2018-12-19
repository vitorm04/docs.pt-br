---
title: '&lt;see&gt; – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 1e799c975fe21dd2dd0354a9d658a271ded5fc2c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235677"
---
# <a name="ltseegt-c-programming-guide"></a>&lt;see&gt; (Guia de Programação em C#)
## <a name="syntax"></a>Sintaxe  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 cref = " `member`"  
 Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual. O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento no XML de saída.Coloque o *membro* entre aspas duplas (" ").  
  
## <a name="remarks"></a>Comentários  
 Use a marca \<see> para especificar um link de dentro do texto. Use [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) para indicar que o texto deve ser colocado em uma seção Consulte também. Use o [atributo cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) para criar hyperlinks internos para páginas de documentação para elementos de código.  
  
 Compile com [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.  
  
 O exemplo a seguir mostra uma marca \<see> dentro de uma seção de resumo.  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
