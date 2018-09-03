---
title: '#region (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 3edc4fe757ab1f5cbf42e67ab74cd8032a82d853
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463267"
---
# <a name="region-c-reference"></a>#region (Referência de C#)
`#region` permite que você especifique um bloco de código que pode ser expandido ou recolhido ao usar o recurso de [estrutura de tópicos](/visualstudio/ide/outlining) do editor do Visual Studio Code. Em arquivos de código mais longos, é conveniente recolher ou ocultar uma ou mais regiões para que você possa se concentrar na parte do arquivo que está trabalhando no momento. O exemplo a seguir mostra como definir uma região:  
  
```csharp
#region MyClass definition  
public class MyClass   
{  
    static void Main()   
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a>Comentários  
 Um bloco `#region` deverá ser encerrado com uma diretiva [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md).  
  
 Um bloco `#region` não pode sobrepor um bloco [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md). No entanto, um bloco `#region` pode ser aninhado em um bloco `#if` e um bloco `#if` pode ser aninhado em um bloco `#region`.  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Diretivas do pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md)
