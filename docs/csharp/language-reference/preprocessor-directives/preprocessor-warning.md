---
title: '##warning – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 38c3807a696599390667060d3bf374c68845fed0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715064"
---
# <a name="warning-c-reference"></a>#warning (Referência de C#)
`#warning` permite gerar um aviso do compilador [CS1030](../../misc/cs1030.md) de nível um de um local específico no código. Por exemplo:   
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Comentários
 Um uso comum de `#warning` é em uma diretiva condicional. Também é possível gerar um erro definido pelo usuário com [#error](./preprocessor-error.md).  
  
## <a name="example"></a>Exemplo  

```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass
{  
    static void Main()
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  

## <a name="see-also"></a>Confira também

- [C# Referência](../index.md)
- [C# Guia de Programação](../../programming-guide/index.md)
- [C# Diretivas de pré-processador](./index.md)
