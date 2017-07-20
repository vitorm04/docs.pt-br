---
title: "Como converter bool? em bool com segurança (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- casting [C#], nullable types
- nullable types [C#], casting bool? to bool
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 7648b9bb5d54b58dc13371e1308f038289df8e56
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-safely-cast-from-bool-to-bool-c-programming-guide"></a>Como converter bool? em bool com segurança (Guia de Programação em C#)
O tipo que permite valor nulo `bool?` pode conter três valores diferentes: `true`, `false` e `null`. Portanto, o tipo `bool?` não pode ser usado em condicionais como com `if`, `for` ou `while`. Por exemplo, o código a seguir gera um erro de compilador.  
  
```  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 Isso não é permitido, porque não está claro o que `null` significa no contexto de uma condicional. Para usar um `bool?` em uma instrução condicional, verifique primeiro sua propriedade <xref:System.Nullable%601.HasValue%2A> para garantir que seu valor não seja `null` e, em seguida, converta-a em `bool`. Para obter mais informações, consulte [bool](../../../csharp/language-reference/keywords/bool.md). Se você executar a conversão em um `bool?` com um valor de `null`, uma <xref:System.InvalidOperationException> será lançada no teste condicional. O exemplo a seguir mostra uma maneira de converter `bool?` em `bool` de maneira segura:  
  
## <a name="example"></a>Exemplo  
  
```csharp  
bool? test = null;  
// Other code that may or may not  
// give a value to test.  
if(!test.HasValue) //check for a value  
{  
    // Assume that IsInitialized  
    // returns either true or false.  
    test = IsInitialized();  
}  
if((bool)test) //now this cast is safe  
{  
   // Do something.  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave literais](../../../csharp/language-reference/keywords/literal-keywords.md)   
 [Tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md)   
 [Operador ??](../../../csharp/language-reference/operators/null-conditional-operator.md)
