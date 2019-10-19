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
ms.openlocfilehash: 57b36bb32e1a575a645f7a15045bf0898dd10dfd
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582211"
---
# <a name="yield-statement-visual-basic"></a>Instrução Yield (Visual Basic)
Envia o próximo elemento de uma coleção para uma instrução `For Each...Next`.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a>Parâmetros  
  
|Termo|Definição|  
|---|---|  
|`expression`|Necessário. Uma expressão que é conversível implicitamente no tipo da função de iterador ou `Get` acessador que contém a instrução `Yield`.|  
  
## <a name="remarks"></a>Comentários  
 A instrução `Yield` retorna um elemento de uma coleção por vez. A instrução `Yield` é incluída em uma função de iterador ou `Get` acessador, que executam iterações personalizadas em uma coleção.  
  
 Você consome uma função de iterador usando um [para cada... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ou uma consulta LINQ. Cada iteração do loop de `For Each` chama a função de iterador. Quando uma instrução `Yield` é atingida na função de iterador, `expression` é retornado e o local atual no código é retido. A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.  
  
 Uma conversão implícita deve existir a partir do tipo de `expression` na instrução `Yield` para o tipo de retorno do iterador.  
  
 Você pode usar uma instrução `Exit Function` ou `Return` para encerrar a iteração.  
  
 "Yield" não é uma palavra reservada e tem um significado especial apenas quando é usado em uma função `Iterator` ou acessador de `Get`.  
  
 Para obter mais informações sobre as funções de iteradores e acessadores `Get`, consulte [iteradores](../../programming-guide/concepts/iterators.md).  
  
## <a name="iterator-functions-and-get-accessors"></a>Funções de iterador e get acessadores  
 A declaração de uma função de iterador ou acessador de `Get` deve atender aos seguintes requisitos:  
  
- Ele deve incluir um modificador de [iterador](../../../visual-basic/language-reference/modifiers/iterator.md) .  
  
- O tipo de retorno deve ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
- Ele não pode ter parâmetros de `ByRef`.  
  
 Uma função de iterador não pode ocorrer em um evento, Construtor de instância, construtor estático ou destruidor estático.  
  
 Uma função de iterador pode ser uma função anônima. Para obter mais informações, consulte [Iteradores](../../programming-guide/concepts/iterators.md).  
  
## <a name="exception-handling"></a>Tratamento de Exceção  
 Uma instrução `Yield` pode estar dentro de um bloco de `Try` de uma [tentativa... Capturar... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Um bloco de `Try` que tem uma instrução `Yield` pode ter blocos de `Catch` e pode ter um bloco de `Finally`.  
  
 Uma instrução `Yield` não pode estar dentro de um bloco de `Catch` ou um bloco de `Finally`.  
  
 Se o corpo de `For Each` (fora da função de iterador) gerar uma exceção, um bloco de `Catch` na função de iterador não será executado, mas um bloco de `Finally` na função de iterador será executado. Um bloco de `Catch` dentro de uma função de iterador captura apenas as exceções que ocorrem dentro da função de iterador.  
  
## <a name="technical-implementation"></a>Implementação Técnica  
 O código a seguir retorna uma `IEnumerable (Of String)` de uma função de iterador e, em seguida, itera pelos elementos da `IEnumerable (Of String)`.  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 A chamada para `MyIteratorFunction` não executa o corpo da função. Em vez disso, a chamada retorna `IEnumerable(Of String)` na variável `elements`.  
  
 Em uma iteração do loop `For Each`, o método <xref:System.Collections.IEnumerator.MoveNext%2A> é chamado para `elements`. Essa chamada executará o corpo de `MyIteratorFunction` até que a próxima instrução `Yield` seja atingida. A instrução `Yield` retorna uma expressão que determina não apenas o valor da variável `element` para consumo pelo corpo do loop, mas também a propriedade <xref:System.Collections.Generic.IEnumerator%601.Current%2A> de elementos, que é uma `IEnumerable (Of String)`.  
  
 Em cada iteração subsequente do loop `For Each`, a execução do corpo do iterador continuará de onde parou, parando novamente quando atingir uma instrução `Yield`. O loop de `For Each` é concluído quando o final da função de iterador ou uma instrução `Return` ou `Exit Function` é atingido.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir tem uma instrução `Yield` que está dentro de um [para... Próximo](../../../visual-basic/language-reference/statements/for-next-statement.md) loop. Cada iteração do corpo da instrução [for each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) no `Main` cria uma chamada para a função de iterador `Power`. Cada chamada à função iteradora prossegue para a próxima execução da instrução `Yield` que ocorre durante a próxima iteração do loop `For…Next`.  
  
 O tipo de retorno do método do iterador é <xref:System.Collections.Generic.IEnumerable%601>, um tipo de interface do iterador. Quando o método iterador é chamado, ele retorna um objeto enumerável que contém as potências de um número.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra um acessador `Get` que é um iterador. A declaração de propriedade inclui um modificador de `Iterator`.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Para obter exemplos adicionais, consulte [iteradores](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Consulte também

- [Instruções](../../../visual-basic/language-reference/statements/index.md)
