---
title: "Como usar a sobrecarga de operador para criar uma classe de número complexo (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- complex numbers [C#]
- classes [C#], operator overloading
- operator overloading [C#], complex numbers
- operator overloading [C#], using to create classes
- operators [C#], overloading to create a complex number class
ms.assetid: c9b8d982-5112-413f-bae3-b42ae3248ddf
caps.latest.revision: 15
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e779d36dcd1d42f7c6c4d3c34c13126666375278
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-operator-overloading-to-create-a-complex-number-class-c-programming-guide"></a>Como usar sobrecarga de operador para criar uma classe de número complexo (Guia de Programação em C#)
Este exemplo mostra como é possível usar a sobrecarga de operador para criar uma classe de número complexo `Complex` que define a adição de complexa. O programa exibe as partes imaginárias e reais dos números e o resultado da adição usando uma substituição do método `ToString`.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-operator-overloading-to-create-a-complex-number-class_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)   
 [operator (Referência de C#)](../../../csharp/language-reference/keywords/operator.md)   
 [Por que os operadores sobrecarregados sempre são estáticos em C#?](http://go.microsoft.com/fwlink/?LinkId=112383)
