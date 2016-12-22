---
title: "Procedimentos gen&#233;ricos no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "métodos genéricos"
  - "métodos genéricos, inferência de tipos"
  - "procedimentos genéricos"
  - "procedimentos genéricos, inferência de tipos"
  - "genéricos [Visual Basic], procedimentos"
  - "genéricos [Visual Basic], inferência de tipos"
  - "procedimentos, genérico"
  - "inferência de tipos"
  - "inferência de tipos, Genéricos"
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Procedimentos gen&#233;ricos no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um  *procedimento genérico* ,também chamado de   *método genérico* , é um procedimento definido com pelo menos um parâmetro de tipo.  Isso permite que o código de chamada adapte os tipos de dados aos seus requisitos sempre que ele chama o procedimento.  
  
 Um procedimento é não genérico simplesmente por diferenciar do que está sendo definido dentro de uma classe genérica ou uma estrutura genérica.  Para ser genérico, o procedimento deve levar pelo menos um parâmetro de tipo, além de qualquer parâmetro normal que ele pode ter.  Uma classe ou estrutura genérica pode conter procedimentos não genéricos e uma classe, estrutura, ou módulo não genéricos podem conter procedimentos genéricos.  
  
 Um procedimento genérico pode usar seus parâmetros de tipo em sua lista parâmetros normais, em seu tipo de retorno se ele tiver um, e em seu código de procedimento.  
  
## Inferência de Tipo  
 Você pode chamar um procedimento genérico sem fornecer quaisquer argumentos de tipo.  Se você chamá\-lo dessa maneira, o compilador tentará determinar os tipos de dados apropriados para passar para os argumentos de tipo do procedimento.  Isso é chamado  *inferência de tipos* .  O código a seguir mostra uma chamada na qual o compilador infere que ele deve passar tipo `String` para o parâmetro de tipo `t`.  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 Se o compilador não puder inferir os argumentos de tipo a partir do contexto de sua chamada, ele relata um erro.  Uma possível causa desse erro é uma incompatibilidade de classificação de matriz.  Por exemplo, suponha que você define um parâmetro normal como uma matriz de um parâmetro do tipo.  Se você chamar o procedimento genérico fornecendo uma matriz de uma posição diferente \(número de dimensões\), a incompatibilidade fará com que inferência de tipos falhe.  O código a seguir mostra uma chamada na qual uma matriz bidimensional é passada para um procedimento que espera um matriz unidimensional.  
  
 `Public Sub demoSub(Of t)(ByVal arg() As t)`  
  
 `End Sub`  
  
 `Public Sub callDemoSub()`  
  
 `Dim twoDimensions(,) As Integer`  
  
 `demoSub(twoDimensions)`  
  
 `End Sub`  
  
 Você pode chamar inferência de tipos somente omitindo todos os argumentos de tipo.  Se você fornecer um argumento de tipo, você deve fornecer todos eles.  
  
 A inferência tipo é suportada somente para procedimentos genéricos.  Você não pode chamar inferência de tipos em classes, estruturas, interfaces ou representantes genéricos.  
  
## Exemplo  
  
### Descrição  
 O exemplo a seguir define um procedimento `Function` genérico para localizar um elemento específico em uma matriz.  Ele define um parâmetro do tipo e usa\-o para construir os dois parâmetros na lista de parâmetros.  
  
### Código  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### Comentários  
 O exemplo anterior requer a capacidade de comparação de `searchValue` com cada elemento de `searchArray`.  Para garantir essa capacidade, ele restringe o parâmetro de tipo `T` para implementar a interface <xref:System.IComparable%601>.  O código usa o método <xref:System.IComparable%601.CompareTo%2A> em vez do operador `=`,porque não há nenhuma garantia de que um argumento de tipo fornecido para `T` oferece suporte ao operador `=`.  
  
 Você pode testar o procedimento `findElement` com o seguinte código:  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 As chamadas anteriores para `MsgBox` exibem "0", "1" e "\-1", respectivamente.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Como definir uma classe capaz de fornecer uma funcionalidade idêntica em tipos de dados diferentes](../Topic/How%20to:%20Define%20a%20Class%20That%20Can%20Provide%20Identical%20Functionality%20on%20Different%20Data%20Types%20\(Visual%20Basic\).md)   
 [Como usar uma classe genérica](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Lista de tipos](../../../../visual-basic/language-reference/statements/type-list.md)   
 [Lista de parâmetros](../../../../visual-basic/language-reference/statements/parameter-list.md)