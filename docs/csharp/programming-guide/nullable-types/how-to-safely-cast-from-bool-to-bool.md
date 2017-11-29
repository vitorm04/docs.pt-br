---
title: "Como converter bool? em bool com segurança (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- casting [C#], nullable types
- nullable types [C#], casting bool? to bool
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a6fa65c15bb5f1da9960dbc17bd25b4087ab862
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
