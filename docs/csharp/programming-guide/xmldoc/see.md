---
title: "&lt;see&gt; (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 065c85ba411794858c8c4d70de0ac1467da1fe56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
  
 Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.  
  
 O exemplo a seguir mostra uma marca \<see> dentro de uma seção de resumo.  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
