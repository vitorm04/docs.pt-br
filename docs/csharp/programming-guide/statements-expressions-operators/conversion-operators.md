---
title: "Operadores de conversão (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c12fd13d6526d79363f973ce2a944c4823bf4104
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="conversion-operators-c-programming-guide"></a>Operadores de conversão (Guia de Programação em C#)
O C# habilita os programadores a declarar conversões em classes ou structs, para que tais classes ou structs possam ser convertidas para e/ou de outras classes ou structs ou tipos básicos. As conversões são definidas como operadores e nomeadas para o tipo para o qual são convertidas. O tipo do argumento a ser convertido ou o tipo do resultado da conversão, mas não ambos, deve ser o tipo recipiente.  
  
 [!code-cs[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## <a name="conversion-operators-overview"></a>Visão Geral dos Operadores de Conversão  
 Os operadores de conversão têm as seguintes propriedades:  
  
-   Conversões declaradas como `implicit` ocorrem automaticamente quando for necessário.  
  
-   Conversões declaradas como `explicit` exigem que uma conversão seja chamada.  
  
-   Todas as conversões devem ser declaradas como `static`.  
  
## <a name="related-sections"></a>Seções relacionadas  
 Para saber mais:  
  
-   [Usando operadores de conversão](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [Transmissões e conversões de tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [Como implementar conversões definidas pelo usuário entre structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [explicit](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [implicit](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [static](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Convert>   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Conversões explícitas encadeadas definidas pelo usuário em C#](http://go.microsoft.com/fwlink/?LinkId=112384)

