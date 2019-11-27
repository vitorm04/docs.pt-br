---
title: Procedimentos genéricos
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
ms.openlocfilehash: 16a629e07cf711778b3d8d1863958ec7a6300649
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350078"
---
# <a name="generic-procedures-in-visual-basic"></a>Procedimentos genéricos no Visual Basic
Um *procedimento genérico*, também chamado de *método genérico*, é um procedimento definido com pelo menos um parâmetro de tipo. Isso permite que o código de chamada Personalize os tipos de dados para seus requisitos cada vez que chama o procedimento.  
  
 Um procedimento não é genérico simplesmente em virtude de ser definido dentro de uma classe genérica ou de uma estrutura genérica. Para ser genérico, o procedimento deve ter pelo menos um parâmetro de tipo, além de quaisquer parâmetros normais que possam ser necessários. Uma classe ou estrutura genérica pode conter procedimentos não genéricos e uma classe, estrutura ou módulo não-genérico pode conter procedimentos genéricos.  
  
 Um procedimento genérico pode usar seus parâmetros de tipo em sua lista de parâmetros normal, em seu tipo de retorno, se tiver um, e em seu código de procedimento.  
  
## <a name="type-inference"></a>Inferência de tipos  
 Você pode chamar um procedimento genérico sem fornecer nenhum argumento de tipo. Se você chamá-lo dessa forma, o compilador tentará determinar os tipos de dados apropriados a serem passados para os argumentos de tipo do procedimento. Isso é chamado de *inferência de tipos*. O código a seguir mostra uma chamada na qual o compilador infere que ele deve passar o tipo `String` para o parâmetro de tipo `t`.  
  
 [!code-vb[VbVbalrDataTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#15)]  
  
 Se o compilador não puder inferir os argumentos de tipo do contexto de sua chamada, ele relatará um erro. Uma possível causa desse erro é uma incompatibilidade de classificação de matriz. Por exemplo, suponha que você defina um parâmetro normal como uma matriz de um parâmetro de tipo. Se você chamar o procedimento genérico fornecendo uma matriz de uma classificação diferente (número de dimensões), a incompatibilidade causará falha na inferência de tipos. O código a seguir mostra uma chamada em que uma matriz bidimensional é passada para um procedimento que espera uma matriz unidimensional.  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 Você pode invocar a inferência de tipos apenas omitindo todos os argumentos de tipo. Se você fornecer um argumento de tipo, deverá fornecer todos eles.  
  
 A inferência de tipos tem suporte apenas para procedimentos genéricos. Não é possível invocar a inferência de tipos em classes, estruturas, interfaces ou delegados genéricos.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir define um procedimento de `Function` genérico para localizar um elemento específico em uma matriz. Ele define um parâmetro de tipo e o usa para construir os dois parâmetros na lista de parâmetros.  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a>Comments  
 O exemplo anterior requer a capacidade de comparar `searchValue` com cada elemento de `searchArray`. Para garantir essa capacidade, ele restringe o parâmetro de tipo `T` para implementar a interface <xref:System.IComparable%601>. O código usa o método <xref:System.IComparable%601.CompareTo%2A> em vez do operador `=`, porque não há nenhuma garantia de que um argumento de tipo fornecido para `T` dá suporte ao operador `=`.  
  
 Você pode testar o procedimento de `findElement` com o código a seguir.  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 As chamadas anteriores para `MsgBox` exibem "0", "1" e "-1", respectivamente.  
  
## <a name="see-also"></a>Consulte também

- [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Como definir uma classe capaz de fornecer uma funcionalidade idêntica em tipos de dados diferentes](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [Como usar uma classe genérica](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Parâmetros e Argumentos de Procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Lista de Tipos](../../../../visual-basic/language-reference/statements/type-list.md)
- [Lista de Parâmetros](../../../../visual-basic/language-reference/statements/parameter-list.md)
