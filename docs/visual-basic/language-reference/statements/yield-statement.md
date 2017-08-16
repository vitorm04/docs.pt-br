---
title: "Instrução yield (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
caps.latest.revision: 22
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 393a9f4de3e801aed5932aef0e2b13d76b003965
ms.lasthandoff: 03/13/2017

---
# <a name="yield-statement-visual-basic"></a>Instrução Yield (Visual Basic)
Envia o próximo elemento de uma coleção para um `For Each...Next` instrução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Yield expression  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Termo|Definição|  
|---|---|  
|`expression`|Necessário. Uma expressão que é implicitamente conversível para o tipo da função iterador ou `Get` acessador que contém o `Yield` instrução.|  
  
## <a name="remarks"></a>Comentários  
 O `Yield` instrução retorna um elemento de uma coleção de cada vez. O `Yield` instrução é incluída em uma função de iterador ou `Get` acessador, que executa iterações personalizadas em uma coleção.  
  
 Consumir uma função de iterador usando um [para cada uma... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ou uma consulta LINQ. Cada iteração de `For Each` loop chama a função do iterador. Quando um `Yield` instrução for alcançada na função iterador, `expression` for retornado, e o local atual no código é retido. A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.  
  
 Deve existir uma conversão implícita de tipo de `expression` no `Yield` instrução para o tipo de retorno do iterador.  
  
 Você pode usar um `Exit Function` ou `Return` instrução para finalizar a iteração.  
  
 "Yield" não é uma palavra reservada e tem um significado especial somente quando ela é usada em uma `Iterator` função ou `Get` acessador.  
  
 Para obter mais informações sobre funções de iterador e `Get` acessadores, consulte [iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
## <a name="iterator-functions-and-get-accessors"></a>Funções de iterador e acessadores Get  
 A declaração de uma função de iterador ou `Get` acessador deve atender aos seguintes requisitos:  
  
-   Ele deve incluir uma [iterador](../../../visual-basic/language-reference/modifiers/iterator.md) modificador.  
  
-   O tipo de retorno deve ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable>  
  
-   Ele não pode ter nenhum `ByRef` parâmetros.  
  
 Uma função do iterador não pode ocorrer em um evento, construtor de instância, construtor estático ou destruidor static.  
  
 Uma função do iterador pode ser uma função anônima. Para obter mais informações, consulte [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
## <a name="exception-handling"></a>Tratamento de Exceção  
 A `Yield` instrução pode ser dentro de uma `Try` bloco de um [Try... Catch... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). A `Try` bloco tem uma `Yield` instrução pode ter `Catch` blocos e pode ter um `Finally` bloco.  
  
 A `Yield` instrução não pode estar dentro de uma `Catch` bloco ou uma `Finally` bloco.  
  
 Se o `For Each` corpo (fora da função de iterador) gera uma exceção, uma `Catch` bloco na função iterador não é executado, mas um `Finally` bloco na função iterador é executado. Um `Catch` bloco dentro de uma função de iterador captura somente exceções que ocorrem dentro da função de iterador.  
  
## <a name="technical-implementation"></a>Implementação Técnica  
 O código a seguir retorna um `IEnumerable (Of String)` de uma função de iterador e itera através dos elementos do `IEnumerable (Of String)`.  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 A chamada para `MyIteratorFunction` não executa o corpo da função. Em vez disso, a chamada retorna `IEnumerable(Of String)` na variável `elements`.  
  
 Em uma iteração de `For Each` loop, o <xref:System.Collections.IEnumerator.MoveNext%2A>método é chamado para `elements`.</xref:System.Collections.IEnumerator.MoveNext%2A> Essa chamada executará o corpo de `MyIteratorFunction` até que a próxima instrução `Yield` seja atingida. O `Yield` instrução retorna uma expressão que determina não apenas o valor da `element` variável para consumo pelo corpo do loop, mas também o <xref:System.Collections.Generic.IEnumerator%601.Current%2A>propriedade de elementos, que é uma `IEnumerable (Of String)`.</xref:System.Collections.Generic.IEnumerator%601.Current%2A>  
  
 Em cada iteração subsequente do loop `For Each`, a execução do corpo do iterador continuará de onde parou, parando novamente quando atingir uma instrução `Yield`. O `For Each` loop é concluído quando o final da função iterador ou uma `Return` ou `Exit Function` instrução seja atingida.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir tem uma `Yield` instrução que está dentro de um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) loop. Cada iteração de [para cada](../../../visual-basic/language-reference/statements/for-each-next-statement.md) corpo da instrução no `Main` cria uma chamada para o `Power` função iterador. Cada chamada à função iteradora prossegue para a próxima execução da instrução `Yield` que ocorre durante a próxima iteração do loop `For…Next`.  
  
 O tipo de retorno do método iterador é <xref:System.Collections.Generic.IEnumerable%601>, um tipo de interface de iterador.</xref:System.Collections.Generic.IEnumerable%601> Quando o método iterador é chamado, ele retorna um objeto enumerável que contém as potências de um número.  
  
 [!code-vb[VbVbalrStatements&#98;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra um acessador `Get` que é um iterador. A declaração de propriedade inclui um `Iterator` modificador.  
  
 [!code-vb[VbVbalrStatements&#99;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 Para obter exemplos adicionais, consulte [iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[vs_dev11_long](../../../csharp/includes/vs_dev11_long_md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)   
 [Instruções](../../../visual-basic/language-reference/statements/index.md)
