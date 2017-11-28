---
title: "#<a name=\"error-c-reference\"></a>error (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#error'
helpviewer_keywords: '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 23528ae81e4ddca23c67c937ca2588ab4c982e98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="error-c-reference"></a>#error (Referência de C#)
O `#error` permite gerar um erro de um local específico em seu código. Por exemplo:  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Comentários  
 Um uso comum de `#error` é em uma diretiva condicional.  
  
 Também é possível gerar um aviso definido pelo usuário com [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).  
  
## <a name="example"></a>Exemplo  
  
```csharp
// preprocessor_error.cs  
// CS1029 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#error DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Diretivas do pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md)
