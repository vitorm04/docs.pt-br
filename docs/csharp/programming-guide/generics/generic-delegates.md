---
title: "Delegados genéricos (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
caps.latest.revision: 16
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
ms.openlocfilehash: be067e2a2e2a192da8ccc92b60af81f0999c449a
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="generic-delegates-c-programming-guide"></a>Delegados genéricos (Guia de Programação em C#)
Um [delegado](../../../csharp/language-reference/keywords/delegate.md) pode definir seus próprios parâmetros de tipo. O código que referencia o delegado genérico pode especificar o argumento de tipo para criar um tipo construído fechado, assim como quando uma classe genérica é instanciada ou quando um método genérico é chamado, conforme mostrado no exemplo a seguir:  
  
 [!code-cs[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]  
  
 A versão 2.0 do C# tem um novo recurso chamado conversão de grupo de método, que pode ser aplicada a tipos concretos e de delegado genérico e habilita a gravação da linha anterior com esta sintaxe simplificada:  
  
 [!code-cs[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]  
  
 Os delegados definidos em uma classe genérica podem usar os parâmetros de tipo da classe genérica da mesma forma que os métodos da classe.  
  
 [!code-cs[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]  
  
 O código que referencia o delegado deve especificar o argumento de tipo da classe recipiente, da seguinte maneira:  
  
 [!code-cs[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]  
  
 Os delegados genéricos são especialmente úteis na definição de eventos com base no padrão de design comum, pois o argumento do remetente pode ser fortemente tipado e não precisa ser convertido de e para <xref:System.Object>.  
  
 [!code-cs[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Generic>   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Introdução aos Genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [Métodos Genéricos](../../../csharp/programming-guide/generics/generic-methods.md)   
 [Classes Genéricas](../../../csharp/programming-guide/generics/generic-classes.md)   
 [Interfaces Genéricas](../../../csharp/programming-guide/generics/generic-interfaces.md)   
 [Delegados](../../../csharp/programming-guide/delegates/index.md)   
 [Genéricos](~/docs/standard/generics/index.md)

