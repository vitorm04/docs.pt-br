---
title: Instrução Yield (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: f938ad29df54ade6722f3de33e931c851ade8c21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604850"
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
 O `Yield` instrução retorna um elemento de uma coleção em uma hora. O `Yield` instrução é incluída em uma função de iterador ou `Get` acessador, que executar iterações personalizadas em uma coleção.  
  
 Você consumir uma função iterator usando um [para cada um... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ou uma consulta LINQ. Cada iteração de `For Each` loop chama a função de iterador. Quando um `Yield` instrução for atingida, a função de iterador, `expression` for retornado, e o local atual no código é retido. A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.  
  
 Deve existir uma conversão implícita de tipo de `expression` no `Yield` instrução para o tipo de retorno do iterador.  
  
 Você pode usar um `Exit Function` ou `Return` instrução para finalizar a iteração.  
  
 "Yield" não é uma palavra reservada e tem um significado especial somente quando ele é usado em uma `Iterator` função ou `Get` acessador.  
  
 Para obter mais informações sobre funções de iterador e `Get` acessadores, consulte [iteradores](../../programming-guide/concepts/iterators.md).  
  
## <a name="iterator-functions-and-get-accessors"></a>Acessadores Get e funções de iterador  
 A declaração da função de um iterador ou `Get` acessador deve atender aos seguintes requisitos:  
  
-   Ele deve incluir um [iterador](../../../visual-basic/language-reference/modifiers/iterator.md) modificador.  
  
-   O tipo de retorno deve ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
-   Ele não pode ter qualquer `ByRef` parâmetros.  
  
 Uma função iterator não pode ocorrer em um evento, construtor de instância, construtor estático ou destruidor estático.  
  
 Uma função de iterador pode ser uma função anônima. Para obter mais informações, consulte [Iteradores](../../programming-guide/concepts/iterators.md).  
  
## <a name="exception-handling"></a>Tratamento de Exceção  
 Um `Yield` instrução pode estar dentro de um `Try` block de um [tente... Catch... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Um `Try` bloco tem um `Yield` instrução pode ter `Catch` bloqueia e pode ter um `Finally` bloco.  
  
 Um `Yield` instrução não pode estar dentro de um `Catch` blocos ou um `Finally` bloco.  
  
 Se o `For Each` corpo (fora da função de iterador) gera uma exceção, uma `Catch` bloco na função iterador não é executado, mas um `Finally` bloco na função de iterador é executado. Um `Catch` blocos dentro de uma função iterator captura somente exceções que ocorrem dentro da função de iterador.  
  
## <a name="technical-implementation"></a>Implementação Técnica  
 O código a seguir retorna um `IEnumerable (Of String)` de uma função iterator e, em seguida, itera por meio dos elementos do `IEnumerable (Of String)`.  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 A chamada para `MyIteratorFunction` não executa o corpo da função. Em vez disso, a chamada retorna `IEnumerable(Of String)` na variável `elements`.  
  
 Em uma iteração do loop `For Each`, o método <xref:System.Collections.IEnumerator.MoveNext%2A> é chamado para `elements`. Essa chamada executará o corpo de `MyIteratorFunction` até que a próxima instrução `Yield` seja atingida. O `Yield` instrução retorna uma expressão que determina não apenas o valor da `element` variável para consumo pelo corpo do loop, mas também o <xref:System.Collections.Generic.IEnumerator%601.Current%2A> propriedades de elementos, que é um `IEnumerable (Of String)`.  
  
 Em cada iteração subsequente do loop `For Each`, a execução do corpo do iterador continuará de onde parou, parando novamente quando atingir uma instrução `Yield`. O `For Each` loop é concluído quando o fim da função iterador ou `Return` ou `Exit Function` instrução for atingida.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir tem um `Yield` instrução que está dentro de um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) loop. Cada iteração do [para cada](../../../visual-basic/language-reference/statements/for-each-next-statement.md) corpo da instrução no `Main` cria uma chamada para o `Power` função iterator. Cada chamada à função iteradora prossegue para a próxima execução da instrução `Yield` que ocorre durante a próxima iteração do loop `For…Next`.  
  
 É o tipo de retorno do método iterador <xref:System.Collections.Generic.IEnumerable%601>, um tipo de interface de iterador. Quando o método iterador é chamado, ele retorna um objeto enumerável que contém as potências de um número.  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra um acessador `Get` que é um iterador. A declaração de propriedade inclui um `Iterator` modificador.  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 Para obter exemplos adicionais, consulte [iteradores](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Consulte também  
 [Instruções](../../../visual-basic/language-reference/statements/index.md)
