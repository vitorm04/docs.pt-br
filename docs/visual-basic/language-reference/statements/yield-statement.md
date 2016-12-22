---
title: "Instru&#231;&#227;o Yield (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Yield"
helpviewer_keywords: 
  - "iteradores, instrução Yield [Visual Basic]"
  - "iteradores [Visual Basic]"
  - "instrução Yield [Visual Basic]"
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Yield (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Envia o próximo elemento de uma coleção para uma declaração de `For Each...Next` .  
  
## Sintaxe  
  
```  
Yield expression  
```  
  
#### Parâmetros  
  
|||  
|-|-|  
|Termo|Definição|  
|`expression`|Obrigatório.  Uma expressão que é implicitamente conversível para o tipo de função do iterador ou acessadores de `Get` que contém a instrução de `Yield` .|  
  
## Comentários  
 A declaração de `Yield` retorna um elemento de uma coleção em vez.  A declaração de `Yield` está incluída em uma função de iterador ou em um acessador de `Get` , que executem iterações personalizados em uma coleção.  
  
 Você consome uma função de iterador usando [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ou consulta LINQ.  Cada iteração do loop de `For Each` chama a função de iterador.  Quando uma declaração de `Yield` é alcançada na função de iterador, `expression` é retornado, e o local atual no código é mantido.  A execução é reiniciada de aquele local na próxima vez que a função de iterador é chamada.  
  
 Uma conversão implícita deve existir do tipo de `expression` na declaração de `Yield` para o tipo de retorno de iterador.  
  
 Você pode usar uma instrução de `Exit Function` ou de `Return` para finalizar a iteração.  
  
 “Produzir” não é uma palavra reservada e tem um significado especial somente quando é usado em uma função de `Iterator` ou em um acessador de `Get` .  
  
 Para obter mais informações sobre funções de iterador e os acessores de `Get` , consulte [Iteradores](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Funções de iterador e obtém acessadores  
 A declaração de uma função de iterador ou um acessador de `Get` deve atender aos seguintes requisitos:  
  
-   Deve incluir um modificador de [Iterador](../../../visual-basic/language-reference/modifiers/iterator.md) .  
  
-   O tipo de retorno deve ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
-   Não pode ter quaisquer parâmetros de `ByRef` .  
  
 Uma função de iterador não pode ocorrer em um evento, em um construtor de instância, em um construtor estático, ou em um destrutor estático.  
  
 Uma função de iterador pode ser uma função anônimo.  Para obter mais informações, consulte [Iteradores](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Manipulação de exceção  
 Uma declaração de `Yield` pode estar dentro de um bloco de `Try` de [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  Um bloco de `Try` que tem uma declaração de `Yield` pode ter blocos de `Catch` , e pode ter um bloco de `Finally` .  
  
 Uma declaração de `Yield` não pode ser dentro de um bloco de `Catch` ou um bloco de `Finally` .  
  
 Se o corpo de `For Each` \(fora da função de iterador\) gera uma exceção, um bloco de `Catch` na função de iterador não é executado, mas um bloco de `Finally` na função de iterador é executado.  Um bloco de `Catch` dentro de uma função de iterador somente captura exceções que ocorrem dentro da função de iterador.  
  
## Implementação técnica  
 O código a seguir retorna `IEnumerable (Of String)` de uma função de iterador e em seguida iterar\-lo através dos elementos de `IEnumerable (Of String)`.  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 A chamada a `MyIteratorFunction` não executa o corpo da função.  Em vez de chamada retorna `IEnumerable(Of String)` na variável de `elements` .  
  
 Em uma iteração do loop de `For Each` de <xref:System.Collections.IEnumerator.MoveNext%2A> , o método é chamado para `elements`.  Esta chamada executa o corpo de `MyIteratorFunction` até que a próxima instrução de `Yield` seja alcançado.  A declaração de `Yield` retorna uma expressão que não apenas determinar o valor da variável de `element` consumíveis pelo corpo de loop mas também da propriedade de <xref:System.Collections.Generic.IEnumerator%601.Current%2A> de elementos, que é `IEnumerable (Of String)`.  
  
 Em cada iteração do loop subsequente de `For Each` , a execução do corpo de iterador continua de onde parou novamente, parando quando atinge uma instrução de `Yield` .  O loop de `For Each` termina quando o final da função de iterador ou de uma instrução de `Return` ou de `Exit Function` é alcançado.  
  
## Exemplo  
 O exemplo tem uma instrução de `Yield` que está dentro de um loop de [For… Next](../../../visual-basic/language-reference/statements/for-next-statement.md) .  Cada iteração do corpo de instrução de [Para cada](../../../visual-basic/language-reference/statements/for-each-next-statement.md) em `Main` cria uma chamada para a função de iterador de `Power` .  Cada chamada à função de iterador continua a seguir execução da declaração de `Yield` , que ocorre durante a próxima iteração do loop de `For…Next` .  
  
 O tipo de retorno do método de iterador é <xref:System.Collections.Generic.IEnumerable%601>, um tipo de interface de iterador.  Quando o método de iterador é chamado, retorna um objeto enumerável que contém a potências de um número.  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## Exemplo  
 O exemplo a seguir demonstra um acessador de `Get` que é um iterador.  A declaração de propriedade inclui um modificador de `Iterator` .  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 Para exemplos adicionais, consulte [Iteradores](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Requisitos  
 [!INCLUDE[vs_dev11_long](../../../csharp/includes/vs_dev11_long_md.md)]  
  
## Consulte também  
 [Iteradores](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)   
 [Instruções](../../../visual-basic/language-reference/statements/index.md)