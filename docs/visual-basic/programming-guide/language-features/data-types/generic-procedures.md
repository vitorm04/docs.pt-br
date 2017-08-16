---
title: "Procedimentos genéricos no Visual Basic | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- generic methods, type inference
- generics [Visual Basic], type inference
- procedures, generic
- generic procedures
- type inference, generics
- generic methods
- type inference
- generics [Visual Basic], procedures
- generic procedures, type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f642b6e2ec984e0de1bd1ce1b4e5e62e0ad1fd26
ms.lasthandoff: 03/13/2017

---
# <a name="generic-procedures-in-visual-basic"></a>Procedimentos genéricos no Visual Basic
A *procedimento genérico*, também chamado um *método genérico*, é um procedimento definido pelo menos um parâmetro de tipo. Isso permite que o código de chamada adapte os tipos de dados para seus requisitos de cada vez que ele chama o procedimento.  
  
 Um procedimento não é genérico simplesmente por que está sendo definido dentro de uma classe genérica ou uma estrutura genérica. Para ser genérico, o procedimento deve levar pelo menos um parâmetro de tipo, além de qualquer parâmetro normal que pode demorar. Uma classe ou estrutura genérica pode conter procedimentos não genéricos e uma classe genérica, estrutura, ou módulo pode conter procedimentos genéricos.  
  
 Um procedimento genérico pode usar seus parâmetros de tipo em sua lista de parâmetros normais, em seu tipo de retorno se ele tiver um e em seu procedimento de código.  
  
## <a name="type-inference"></a>Inferência de tipos  
 Você pode chamar um procedimento genérico sem fornecer quaisquer argumentos de tipo algum. Se você chamá-lo dessa maneira, o compilador tentará determinar os tipos de dados apropriados para passar para os argumentos de tipo do procedimento. Isso é chamado de *inferência de tipo*. O código a seguir mostra uma chamada na qual o compilador infere que ele deve passar tipo `String` para o parâmetro de tipo `t`.  
  
 [!code-vb[VbVbalrDataTypes&#15;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 Se o compilador não pode inferir os argumentos de tipo do contexto de sua chamada, ele relata um erro. Uma possível causa desse erro é uma incompatibilidade de classificação de matriz. Por exemplo, suponha que você define um parâmetro normal como uma matriz de um parâmetro de tipo. Se você chamar o procedimento genérico fornecendo uma matriz de uma posição diferente (número de dimensões), a incompatibilidade fará com que inferência falha. O código a seguir mostra uma chamada na qual uma matriz bidimensional é passada para um procedimento que espera uma matriz unidimensional.  
  
 `Public Sub demoSub(Of t)(ByVal arg() As t)`  
  
 `End Sub`  
  
 `Public Sub callDemoSub()`  
  
 `Dim twoDimensions(,) As Integer`  
  
 `demoSub(twoDimensions)`  
  
 `End Sub`  
  
 Você pode chamar inferência de tipos somente omitindo todos os argumentos de tipo. Se você fornecer um argumento de tipo, você deve fornecer todos eles.  
  
 Inferência de tipo é suportada somente para procedimentos genéricos. Você não pode chamar inferência de tipo em classes genéricas, estruturas, interfaces ou representantes.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir define um genérico `Function` procedimento para localizar um elemento específico em uma matriz. Ele define um parâmetro do tipo e usa-o para construir os dois parâmetros na lista de parâmetros.  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbalrDataTypes&#14;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a>Comentários  
 O exemplo anterior requer a capacidade de comparar `searchValue` com cada elemento de `searchArray`. Para garantir essa capacidade, ele restringe o parâmetro de tipo `T` para implementar o <xref:System.IComparable%601>interface.</xref:System.IComparable%601> O código usa o <xref:System.IComparable%601.CompareTo%2A>método em vez do `=` operador, porque não há nenhuma garantia de que um argumento de tipo fornecido para `T` oferece suporte a `=` operador.</xref:System.IComparable%601.CompareTo%2A>  
  
 Você pode testar o `findElement` procedimento com o código a seguir.  
  
 [!code-vb[VbVbalrDataTypes&13;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 As chamadas anteriores para `MsgBox` exibem "0", "1" e "-1", respectivamente.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Como: definir uma classe que pode fornecer funcionalidade idêntica em diferentes tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)   
 [Como: usar uma classe genérica](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Argumentos e parâmetros de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Lista de tipos](../../../../visual-basic/language-reference/statements/type-list.md)   
 [Lista de Parâmetros](../../../../visual-basic/language-reference/statements/parameter-list.md)
