---
title: '#undef (Referência de C#)'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 3957d58f61e51fab01618f5e1146be9cd0da58fd
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46525562"
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

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Diretivas do pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md)
