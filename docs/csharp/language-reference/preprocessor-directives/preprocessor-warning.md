---
title: '#warning (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 59ca63d5089e377627a9116f24f9a0a1681bb4b2
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932671"
---
# <a name="warning-c-reference"></a>#warning (Referência de C#)
`#warning` permite gerar um aviso do compilador [CS1030](../../misc/cs1030.md) de nível um de um local específico no código. Por exemplo:  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Comentários
 Um uso comum de `#warning` é em uma diretiva condicional. Também é possível gerar um erro definido pelo usuário com [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).  
  
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

## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Diretivas do pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md)
