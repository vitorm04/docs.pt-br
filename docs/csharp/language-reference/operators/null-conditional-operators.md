---
title: Operadores condicionais nulos (C# e Visual Basic)
ms.date: 04/03/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- null-conditional operators [C#]
- null-conditional operators [Visual Basic]
- ?. operator [C#]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3ffeaa3c2088d0bb2c000704cfe312b0f9453b68
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a>?. Operadores condicionais nulos ?. e ?[] (C# e Visual Basic)
Usado para testar a presença de nulos antes de executar uma operação de acesso de membro (`?.`) ou de índice (`?[]`).  Esses operadores ajudam a escrever menos código para lidar com verificações de nulidade, especialmente para entrar em estruturas de dados.  
  
```csharp  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
```  
  
```vb  
Dim length = customers?.Length  ' null if customers is null  
Dim first as Customer = customers?(0)  ' null if customers is null  
Dim count as Integer? = customers?(0)?.Orders?.Count()  ' null if customers, the first customer, or Orders is null  
```  
  
 Os operadores condicionais estão entrando em curto-circuito.  Se uma operação em uma cadeia de operações de índice e acesso de membro condicionais retornar nulo, o restante da execução da cadeia será interrompido.  No exemplo a seguir, `E` não será executado se `A`, `B` ou `C` for avaliado como nulo.
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
 Outro uso para o acesso de membro condicional nulo é invocar representantes de forma thread-safe com muito menos código.  A maneira antiga requer código semelhante ao seguinte:  
  
```csharp  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…);
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```  
  
 A nova maneira é muito mais simples:  
  
```csharp
PropertyChanged?.Invoke(e)  
```  

```vb
PropertyChanged?.Invoke(e)
```  
  
 A nova forma é thread-safe porque o compilador gera código para avaliar `PropertyChanged` somente uma vez, mantendo o resultado em uma variável temporária.  
  
 Você precisa chamar explicitamente o método `Invoke` porque não há nenhuma sintaxe de invocação de delegado condicional nulo `PropertyChanged?(e)`.  
  
## <a name="language-specifications"></a>Especificações da linguagem  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 Para obter mais informações, consulte [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md).  
  
## <a name="see-also"></a>Consulte também  
 [?? (operador de união nula)](null-conditional-operator.md)  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md)  
 [Guia de programação do Visual Basic](../../../visual-basic/programming-guide/index.md)
