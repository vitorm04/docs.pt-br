---
title: "#<a name=\"warning-c-reference\"></a>warning (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#warning'
dev_langs:
- CSharp
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
caps.latest.revision: 9
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
ms.openlocfilehash: 8630101a90bd6d4ed2036b495b254c9475531dc0
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="warning-c-reference"></a>#warning (Referência de C#)
O `#warning` permite gerar um aviso de um nível um em um local específico em seu código. Por exemplo:  
  
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
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Diretivas do pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md)

