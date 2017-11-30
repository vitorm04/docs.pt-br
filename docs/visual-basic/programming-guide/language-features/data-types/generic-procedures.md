---
title: "Procedimentos genéricos no Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e019ca32277f93f798e99e996a3670c8302ba9b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-procedures-in-visual-basic"></a>Procedimentos genéricos no Visual Basic
Um *procedimento genérico*, também chamado um *método genérico*, é um procedimento definido pelo menos um parâmetro de tipo. Isso permite que o código de chamada personalizar os tipos de dados para seus requisitos de cada vez que ele chama o procedimento.  
  
 Um procedimento não é genérico simplesmente em virtude do que está sendo definido dentro de uma classe genérica ou uma estrutura genérica. Para ser genérico, o procedimento deve levar pelo menos um parâmetro de tipo, além de qualquer parâmetro normal pode demorar. Uma classe ou estrutura genérica pode conter procedimentos não genéricos e uma classe não-genérica, estrutura, ou módulo pode conter procedimentos genéricos.  
  
 Um procedimento genérico pode usar seus parâmetros de tipo em sua lista de parâmetros normais, em seu tipo de retorno se ele tiver um código de um e em seu procedimento.  
  
## <a name="type-inference"></a>Inferência de tipos  
 Você pode chamar um procedimento genérico sem fornecer quaisquer argumentos de tipo em todos os. Se você chamá-lo dessa forma, o compilador tentará determinar os tipos de dados apropriados para passar para os argumentos de tipo do procedimento. Isso é chamado de *inferência de tipo*. O código a seguir mostra uma chamada na qual o compilador infere que ele deve passar tipo `String` para o parâmetro de tipo `t`.  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 Se o compilador não é possível inferir os argumentos de tipo do contexto de sua chamada, ele relatará um erro. Uma possível causa desse erro é uma incompatibilidade de classificação de matriz. Por exemplo, suponha que você define um parâmetro normal como uma matriz de um parâmetro de tipo. Se você chamar o procedimento genérico fornecendo uma matriz de uma posição diferente (número de dimensões), a incompatibilidade fará com que inferência falhar. O código a seguir mostra uma chamada na qual uma matriz bidimensional é passada para um procedimento que espera uma matriz unidimensional.  
  
 `Public Sub demoSub(Of t)(ByVal arg() As t)`  
  
 `End Sub`  
  
 `Public Sub callDemoSub()`  
  
 `Dim twoDimensions(,) As Integer`  
  
 `demoSub(twoDimensions)`  
  
 `End Sub`  
  
 Você pode chamar inferência de tipos somente omitindo todos os argumentos de tipo. Se você fornecer um argumento de tipo, você deve fornecer todos eles.  
  
 Inferência de tipo tem suporte somente para procedimentos genéricos. Não é possível chamar inferência de tipo em classes genéricas, estruturas, interfaces ou delegados.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir define um genérico `Function` procedimento para localizar um elemento específico em uma matriz. Ele define um parâmetro de tipo e usa para construir os dois parâmetros na lista de parâmetros.  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a>Comentários  
 O exemplo anterior requer a capacidade de comparar `searchValue` com cada elemento de `searchArray`. Para garantir essa capacidade, ela restringe o parâmetro de tipo `T` para implementar o <xref:System.IComparable%601> interface. O código usa o <xref:System.IComparable%601.CompareTo%2A> método em vez do `=` operador, porque não há nenhuma garantia de que um argumento de tipo fornecido para `T` oferece suporte a `=` operador.  
  
 Você pode testar o `findElement` procedimento com o código a seguir.  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 As chamadas anteriores para `MsgBox` exibem "0", "1" e "-1", respectivamente.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Como definir uma classe capaz de fornecer uma funcionalidade idêntica em tipos de dados diferentes](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [Como usar uma classe genérica](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Parâmetros e Argumentos de Procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Lista de Tipos](../../../../visual-basic/language-reference/statements/type-list.md)  
 [Lista de Parâmetros](../../../../visual-basic/language-reference/statements/parameter-list.md)
