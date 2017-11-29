---
title: "&lt;seealso&gt; (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 088445680375e1c1805f9fb4356fe98c730178e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltseealsogt-c-programming-guide"></a>&lt;seealso&gt; (Guia de Programação em C#)
## <a name="syntax"></a>Sintaxe  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 cref = " `member`"  
 Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual. O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento no XML de saída.`member` deve ser exibido entre aspas duplas (" ").  
  
 Para obter informações sobre como criar uma referência cref para um tipo genérico, consulte [ \<consulte>](../../../csharp/programming-guide/xmldoc/see.md).  
  
## <a name="remarks"></a>Comentários  
 A marca \<seealso > permite especificar o texto que você quer que seja exibido na seção Ver também. Use [\<see>](../../../csharp/programming-guide/xmldoc/see.md) para especificar um link de dentro do texto.  
  
 Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Consulte [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) para obter um exemplo sobre o uso de \<seealso>.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
