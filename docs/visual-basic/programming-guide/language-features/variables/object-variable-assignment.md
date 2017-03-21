---
title: "Atribuição de variável (Visual Basic) do objeto | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Nothing keyword, object variable assignment
- object variables, initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables, assigning
- variables [Visual Basic], object variables
- current instance, defined
- variables [Visual Basic], assigning
- assignment statements, object variable assignment
- Me keyword, as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 08fe7f56115f76406acac4d49594f572802bb647
ms.lasthandoff: 03/13/2017

---
# <a name="object-variable-assignment-visual-basic"></a>Atribuição de variável do objeto (Visual Basic)
Você pode usar uma instrução de atribuição normal para atribuir um objeto a uma variável de objeto. Você pode atribuir uma expressão de objeto ou o [nada](../../../../visual-basic/language-reference/nothing.md) palavra-chave, como o exemplo a seguir ilustra.  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 `Nothing`significa que não há nenhum objeto atualmente atribuído à variável.  
  
## <a name="initialization"></a>Inicialização  
 Quando seu código começa a executar, seu objeto variáveis são inicializadas como `Nothing`. Aqueles cujas declarações incluem inicialização são reinicializadas para os valores que você especifica quando as instruções de declaração são executadas.  
  
 Você pode incluir a inicialização na sua declaração usando o [novo](../../../../visual-basic/language-reference/operators/new-operator.md) palavra-chave. As seguintes instruções de declaração declaram variáveis de objeto `testUri` e `ver` e atribuem objetos específicos a elas. Cada uma usa um dos construtores sobrecarregados da classe apropriada para inicializar o objeto.  
  
```  
Dim testUri As New System.Uri("http://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a>Dissociação  
 Definindo uma variável de objeto `Nothing` interrompe a associação da variável com qualquer objeto específico. Isso impede que você altere acidentalmente o objeto alterando a variável. Ele também permite testar se a variável de objeto aponta para um objeto válido, como mostra o exemplo a seguir.  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 Se o objeto que sua variável se refere estiver em outro aplicativo, esse teste não pode determinar se esse aplicativo foi finalizado ou simplesmente invalidou o objeto.  
  
 Uma variável de objeto com um valor de `Nothing` também é chamado de um *nulo de referência*.  
  
## <a name="current-instance"></a>Instância atual  
 O *atual instância* de um objeto é aquele no qual o código está sendo executado. Como todo o código é executado dentro de um procedimento, a instância atual é aquele no qual o procedimento foi chamado.  
  
 O `Me` palavra-chave atua como uma variável de objeto referindo-se à instância atual. Se um procedimento não é [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md), pode usar o `Me` palavra-chave para obter um ponteiro para a instância atual. Procedimentos compartilhados não podem ser associados uma instância específica de uma classe.  
  
 Usando `Me` é particularmente útil para passar a instância atual para um procedimento em outro módulo. Por exemplo, suponha que você tem um número de documentos XML e deseja adicionar um texto padrão para todos eles. O exemplo a seguir define um procedimento para fazer isso.  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 Cada objeto de documento XML poderia, em seguida, chame o procedimento e passar sua instância atual como um argumento. O exemplo a seguir demonstra isso.  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a>Consulte também  
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Declaração de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Valores de variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Como: declarar uma variável de objeto e atribuir um objeto a ela no Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)   
 [Como: fazer um objeto variável não se referir a qualquer instância](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)   
 [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
