---
title: "#<a name=\"undef-c-reference\"></a>undef (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#undef'
dev_langs:
- CSharp
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: acdd043535ef319f2af40c809e7fe4af612cb17d
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="undef-c-reference"></a>#undef (Referência de C#)
`#undef` permite excluir as definições de um símbolo, de modo que, usando o símbolo como a expressão em uma diretiva [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), a expressão será avaliada como `false`.  
  
 Um símbolo pode ser definido com a diretiva [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) ou com a opção do compilador [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md). A diretiva `#undef` deve ser exibida no arquivo antes de usar qualquer instrução que também não sejam diretivas.  
  
## <a name="example"></a>Exemplo  
  
```csharp
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass   
{  
    static void Main()   
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```  
  
 **DEBUG não está definido**   
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Diretivas do pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md)

