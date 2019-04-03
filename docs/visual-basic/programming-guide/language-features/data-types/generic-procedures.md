---
title: Procedimentos genéricos no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: 4aed16ce9eb59da54156a0cd5f1594819788521b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818911"
---
# <a name="generic-procedures-in-visual-basic"></a>Procedimentos genéricos no Visual Basic
Um *procedimento genérico*, também chamado um *método genérico*, é um procedimento definido pelo menos um parâmetro de tipo. Isso permite que o código de chamada personalizar os tipos de dados para seus requisitos de cada vez que ele chama o procedimento.  
  
 Um procedimento não é genérico simplesmente em virtude de que está sendo definido dentro de uma classe genérica ou uma estrutura genérica. Para ser genérico, o procedimento tenha pelo menos um parâmetro de tipo, além de quaisquer parâmetros normais, pode levar. Uma classe genérica ou estrutura pode conter procedimentos não genéricos e uma classe não genérica, estrutura, ou módulo pode conter procedimentos genéricos.  
  
 Um procedimento genérico pode usar seus parâmetros de tipo na lista de parâmetros normais, em seu tipo de retorno se ele tiver um e em seu procedimento de código.  
  
## <a name="type-inference"></a>Inferência de tipos  
 Você pode chamar um procedimento genérico sem fornecer quaisquer argumentos de tipo em todos os. Se você chamá-lo dessa forma, o compilador tentará determinar os tipos de dados apropriado para passar para os argumentos de tipo do procedimento. Isso é chamado *inferência de tipo*. O código a seguir mostra uma chamada na qual o compilador infere que ele deve passar o tipo `String` para o parâmetro de tipo `t`.  
  
 [!code-vb[VbVbalrDataTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#15)]  
  
 Se o compilador não é possível inferir os argumentos de tipo do contexto de sua chamada, ele relatará um erro. Uma possível causa desse erro é uma incompatibilidade de classificação de matriz. Por exemplo, suponha que você definir um parâmetro normal como uma matriz de um parâmetro de tipo. Se você chamar o procedimento genérico fornecendo uma matriz de uma classificação diferente (número de dimensões), a incompatibilidade faz com que a inferência de tipo falhar. O código a seguir mostra uma chamada em que uma matriz bidimensional é passada para um procedimento que espera uma matriz unidimensional.  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 Você pode invocar a inferência de tipo omitindo todos os argumentos de tipo. Se você fornecer um argumento de tipo, você deve fornecer todos eles.  
  
 Inferência de tipo tem suporte apenas para procedimentos genéricos. Você não pode invocar a inferência de tipo em classes genéricas, estruturas, interfaces ou delegados.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir define um genérico `Function` procedimento para localizar um elemento específico em uma matriz. Ele define um parâmetro de tipo e usa-o para construir os dois parâmetros na lista de parâmetros.  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a>Comentários  
 O exemplo anterior requer a capacidade de comparar `searchValue` com cada elemento de `searchArray`. Para garantir essa capacidade, ela restringe o parâmetro de tipo `T` para implementar o <xref:System.IComparable%601> interface. O código usa o <xref:System.IComparable%601.CompareTo%2A> método em vez do `=` operador, porque não há nenhuma garantia de que um argumento de tipo fornecido para `T` dá suporte a `=` operador.  
  
 Você pode testar o `findElement` procedimento com o código a seguir.  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 As chamadas anteriores para `MsgBox` exibir "0", "1" e "-1", respectivamente.  
  
## <a name="see-also"></a>Consulte também

- [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Como: definir uma classe capaz de fornecer uma funcionalidade idêntica em tipos de dados diferentes](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [Como: usar uma classe genérica](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Parâmetros e Argumentos de Procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Lista de Tipos](../../../../visual-basic/language-reference/statements/type-list.md)
- [Lista de Parâmetros](../../../../visual-basic/language-reference/statements/parameter-list.md)
